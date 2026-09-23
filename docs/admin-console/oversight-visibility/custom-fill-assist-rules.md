# 自定义填充辅助规则

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/custom-fill-assist-rules/)
{% endhint %}

企业版组织可以使用[使用策略](enterprise-policies.md#activate-fill-assist)为成员设置默认的[填充辅助](../../password-manager/autofill/more-autofill-options/fill-assist.md)状态，以及（可选）使用组织托管和维护的规则集替换 Bitwarden 精选的填充辅助规则。

本文介绍如何构建自定义规则集。有关填充辅助和相关策略的实际应用，请参阅上方链接中的文章。

## 自定义规则集 <a href="#custom-rulesets" id="custom-rulesets"></a>

默认情况下，填充辅助使用由 Bitwarden 精选的规则集。您可能希望在此基础上进行改进，或替换该规则集，以扩大对组织成员最常使用的网站和应用程序的覆盖范围。例如，内部网站就是构建和维护自定义规则集的一个充分理由。

### 规则集内容 <a href="#ruleset-contents" id="ruleset-contents"></a>

自定义规则集是一个**目录** ，而不是单个文件。当您为策略提供**自定义自动填充规则集** URL 时，必须提供指向该**目录**的链接。使用填充辅助的客户端期望规则集目录中包含四个文件：

* `forms.v1.json`：您的规则数据。
* `forms.v1.schema.json`：您的规则数据的架构。
* `manifest.json`：构建元数据和每个映射的架构版本。
* `manifest.schema.json`：清单的架构。

您的自定义规则集必须通过 HTTPS 提供给客户端。客户端将每 6 小时重新获取一次规则集，以确保您的成员获得最新的规则。

### 规则集中的规则 <a href="#rules-in-the-ruleset" id="rules-in-the-ruleset"></a>

{% hint style="success" icon="lightbulb" %}
我们将在本文中介绍规则创建的基础知识，但由 Bitwarden 维护的 [Map the Web](https://github.com/bitwarden/map-the-web/) 仓库包含了关于规则结构的完整信息。我们建议在编写自定义规则时参考该仓库的 README。
{% endhint %}

规则使用 JSON 编写。每条规则位于一个 `host`（即域名）下，并使用 CSS 选择器描述该主机页面上的表单。

```json
{
  "schemaVersion": "1.0.0",
  "hosts": {
    "example.com": {
      "forms": [
        {
          "category": "account-login",
          "container": ["form#login-form"],
          "fields": {
            "username": ["input#email"],
            "password": ["input#password"]
          },
          "actions": {
            "submit": ["button[type='submit']"]
          }
        }
      ]
    }
  }
}
```

一条规则通常包含四个部分：

<table><thead><tr><th width="115.199951171875">键</th><th width="385.4000244140625">值</th><th>是否必需？</th></tr></thead><tbody><tr><td><code>category</code></td><td>这是什么类型的表单，<code>account-login</code>、<code>account-creation</code>、<code>payment-card</code>、<code>address</code> 等等</td><td>是</td></tr><tr><td><code>container</code></td><td>包裹表单的元素，通常是 <code>&#x3C;form></code> 标签。</td><td>否</td></tr><tr><td><code>fields</code></td><td>一组固定的键，映射到一个或多个 CSS 选择器。更多信息，请参阅以下部分</td><td>是</td></tr><tr><td><code>actions</code></td><td>按钮或其他交互元素，例如 <code>submit</code> 或 <code>next</code></td><td>否</td></tr></tbody></table>

当某个主机拥有多个结构不同的表单时，请将 `pathnames` 添加到特定规则，这些规则将取代该主机的全局规则：

```json
"example.com": {
  "forms": [ /* the rule for every other page */ ],
  "pathnames": {
    "/login": {
      "forms": [ /* a completely different rule, just for this page */ ]
    }
  }
}
```

#### 字段 <a href="#fields" id="fields"></a>

字段将一组固定的键（例如 `username`、`password`、`email`、`firstName` 和 `cardNumber`）与以相应值表示的 CSS 选择器关联起来，例如：

```json
"fields": {
  "username": ["input#email"],
  "password": ["input#password"]
}
```

在此示例中，`username` 是从可用选项的离散列表中选择的键，`input#email` 是 CSS 选择器，以数组形式表示，因为字段键可能映射到多个选择器：

```json
"username": ["input#email", "input[autocomplete='username']"]
```

{% hint style="success" icon="lightbulb" %}
编写字段时，需要**刻意使其具有一定的脆弱性**。每个选择器都记录了特定字&#x6BB5;_&#x5F53;前&#x7684;_&#x7CBE;确状态。如果其下方的页面发生更改，您希望规则**失效**而不是自动调整，以此来明确地提示需要人工审核。如果选择器在页面更改后仍然保持匹配，那么它很可能指向了错误的内容，而没有任何机制可以捕获这种错误。
{% endhint %}

## 构建自定义规则集 <a href="#build-a-custom-ruleset" id="build-a-custom-ruleset"></a>

要构建自定义规则集，推荐的操作流程如下：

1. 创建 `github.com/bitwarden/map-the-web` 仓库的分支。
2. 在分支中，编辑 `maps/forms/forms.jsonc` 以满足您组织的需求。建议保留现有条目不变，并按照上一节中的格式说明添加新条目。
3. 使用 `npm run check && npm run build` 进行验证和构建。构建通过后，将生成客户端所需的压缩工件和清单文件。
4. 发布构建工件，确保所有四个预期文件都位于同一个可通过 HTTPS 访问的目录中。GitHub Release 就是一个很好的例子，它提供了一种简单直接的方法来实现这一点。
5. 将您的策略的**自定义自动填充规则集**指向该可通过 HTTPS 访问的目录，如果您使用云托管，可以[通过 UI 操作](enterprise-policies.md#activate-auto-fill)；如果您是自托管，可以[使用环境变量](../../self-hosting/deploy-and-configure/configuration-options/environment-variables.md#optional-variables)。如果您使用 GitHub，这看起来会类似于 `https://github.com/<your-org>/forked-map-the-web/releases/latest/download/`。

## 维护自定义规则集 <a href="#maintain-a-custom-ruleset" id="maintain-a-custom-ruleset"></a>

按照本文档所述的方式使用自定义规则集将完全替换 Bitwarden 精选的规则集，保持您的分支为最新版本是您的责任。请注意，如果某个分支没有定期与上游维护的仓库同步，随着 Bitwarden 不断添加和修正规则，它会悄然产生偏差。请定期拉取上游变更。

### 规则集验证 <a href="#ruleset-validation" id="ruleset-validation"></a>

目前没有错误报告机制可以检测出格式错误的规则集。如果您的规则集 URL 无法访问、返回错误或提供无效的 JSON，填充辅助将不会对受影响的成员执行任何操作，也不会回退到 Bitwarden 精选的规则集。要验证您的规则集是否正常工作：

1. 在浏览器中直接打开这四个文件，确认它们通过 HTTPS 返回有效的 JSON。
2. 确认 `manifest.json` 报告的是您期望的架构版本。
3. 请在规则集已涵盖的页面上进行测试。客户端每 6 小时才会重新获取一次，因此在重新测试之前，请留出时间让修复生效。
4. 如果您不确定自定义规则集是否是问题的原因，请暂时将策略指向 Bitwarden 的默认规则 URL，以隔离问题。

### 版本固定 <a href="#version-pinning" id="version-pinning"></a>

在 Bitwarden Admin Console 中设置策略时，需要一个 URL，但您使用的 URL 会决定您对规则集更改何时到达成员客户端的控制程度。如果您使用的是 GitHub Releases，则至少有两种选择：

1.  **始终使用最新版本**。将 URL 设置为以下地址，以便客户端始终获取您最新发布的工件。如果您希望自动将修复程序和新增代码覆盖范围推送给客户端，这将非常有用。

    ```
    https://github.com/<your-org>/forked-map-the-web/releases/latest/download/
    ```
2.  **固定版本**。将 URL 设置为以下地址，这样客户端将始终使用该工件的特定版本，直到您在 Bitwarden Admin Console 中更新该字段为止。这有助于实现更高级别的控制。

    ```
    https://github.com/<your-org>/forked-map-the-web/releases/download/v20260904.1/
    ```

### 安全考量 <a href="#security-considerations" id="security-considerations"></a>

使用自定义规则集时，您的组织负责规则的安全性和正确性。Bitwarden 不会审核、审查或验证自定义规则或规则集，也不会保证内容按原样获取并应用于成员的客户端。所有自定义规则集的实施都应：

* 使用您的组织控制的基础设施进行托管。
* 将该位置的写入权限视为敏感权限。
* 在发布新的工件版本之前，应包含一个审查规则变更的流程。

请注意，如果规则集遭到破坏或疏忽，则所有启用了填充辅能的用户，以及所有设置了这些规则的网站，其自动填充行为都会受到影响。为了修复损坏或设计不佳的表单上的自动填充问题，填充辅助规则可以有意绕过字段可见性检查、字段类型检查和点击劫持防护。这意味着恶意或编写不当的规则可能导致凭据被填充到不应填充的位置。

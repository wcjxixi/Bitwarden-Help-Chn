# 调用的加密库

{% hint style="success" %}
对应的[官方文档地址](https://bitwarden.com/help/kdf-algorithms/)
{% endhint %}

Bitwarden 不实现任何密码原语。Bitwarden 仅采用由密码学专家编写并维护的、广受欢迎且信誉良好的密码库中的密码原语。使用了以下加密库：

* JavaScript:
  * [Web crypto](https://www.w3.org/TR/WebCryptoAPI/)
  * [Node.js crypto](https://nodejs.org/api/crypto.html)
  * [Forge](https://github.com/digitalbazaar/forge)
  * [Argon2](https://github.com/antelle/argon2-browser)
* Rust Crates:
  * [RustCrypto](https://github.com/rustcrypto)
  * [curve25519-dalek](https://github.com/dalek-cryptography/curve25519-dalek)
  * [rust-random](https://github.com/rust-random/)
  * [rustls](https://github.com/rustls/rustls)

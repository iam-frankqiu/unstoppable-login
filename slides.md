---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Unstoppable login findings

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/iam-frankqiu/slidev-template" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# What is Unstoppable Login?

<div class="flex justify-center">
<img src="/images/login-promo.png" style="width: 40vw;" />
</div>

Login with Unstoppable allows owners of Unstoppable Domains to log in and share profile information with EVM-compatible applications. This gives users more control over their personal information and allows developers to access information about their users without needing to host or maintain a CRM database.

<br>
<br>


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>


---

# Process

<div class="flex justify-center">
<img src="/images/login-with-unstoppable-flow-revised.png" style="width: 40vw;" />
</div>


---

# Benefits

### Benefits for Applications

- Avoid hosting a database of user contact information by requesting access only when it's needed.
- Request additional data from users such as social profiles to further enhance the user experience.
- Communicate with users directly via opt-in access and the @ud.me proxy email service.

### Benefits for Users

- Maintain absolute control over login credentials.
- Sharing personal information is 100% opt-in.
- Receive email communications without sharing private email addresses.
- Only one login for every web3 app. No need to remember multiple unique usernames and passwords.

---

# Limitations

### Supported TLDs

Login with Unstoppable currently supports the following top-level domains (TLDs):

```
.crypto
.nft
.blockchain
.bitcoin
.wallet
.888
.dao
.x
.klever
.zil *
```

### Considerations

The components provided by the UAuth libraries are only available in React. The UAuth modal is written in React, which has a larger library size.





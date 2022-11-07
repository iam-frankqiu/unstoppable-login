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
<img src="/images/login-with-unstoppable-flow-revised.png" style="width: 35vw;" />
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

---

# Featured Updates

### Login with Verified Solana Wallet

Applications can confirm that a user authenticated with a Solana address using the getAuthorizationAccount() method of UAuth.

```
const authorization = await uauth.loginWithPopup();
const account = uauth.getAuthorizationAccount(authorization);
```

The VerifiedAddress returned for a Login session authorized by a Solana wallet would look something like this:


```
{
  address: 'Ft2Z5NocHXD61jHzSkzk8qpVkMETDETitoyei6QQDXt4', // The verified solana address
  message: 'Link Unstoppable Domain domain.tld with secondary wallet.\n    \n    {\n  "domain": "domain.tld",\n  "currency": "SOL",\n  "wallet": "Ft2Z5NocHXD61jHzSkzk8qpVkMETDETitoyei6QQDXt4"\n}',
  signature: '27D5QwhpVZCEFPxQBNCkTb8NKKL7gKEaRqCitiXTC1BF2n1Bdd3MReBGXaE2yi1Cz683hDchvEBuTXaHTVbc83q',
  symbol: 'SOL',
},
```

---

# Getting Started

### 1.Get Your Client Credentials

<video loop autoplay muted src="https://docs.unstoppabledomains.com/videos/connect-wallet-and-create-client.mp4"></video>

---

- Go to the Client Management Dashboard .
- Click the Connect Wallet and sign the transaction.
- Click the Create Client button to add a new client.

Once you've created your client, you will need the Client Metadata to configure your UAuth application. This can be copied directly from the Login page of your Client Configuration.

```
{
    clientID: "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    redirectUri: "http://localhost",
    scope: "openid wallet",
}

```

---

### 2: Choose Your Integration Path

<div class="flex justify-center">
<img src="/images/integration_guide.png" style="width: 40vw;" />
</div>

---

### 3: Configure the Login UI

Step 1: Access User Information

```
import UAuth from '@uauth/js'

const uauth = new UAuth({
  // ... options
})

uauth.user()
  .then((user) => {
    // user exists
    console.log("User information:", user)
  })
  .catch(() => {
    // user does not exist
  })
  ```

  ```

{
  "sub" : "domain.tld", // The domain used to login
  "wallet_address" : "0x . . . ", // The Ethereum wallet that owns the domain
  "wallet_type_hint" : "web3",
  "eip4361_message" : "identity.unstoppable domains wants you sign in with your Ethereum account: . . . ",
  "eip4361_signature" : "0x . . . ",
}

  ```
---

### Step 2: Get the Authorization Account

In addition to logging in with the controlling Ethereum or Polygon wallet, UAuth service allows users to login using certain verified accounts associated with the domain's ud.me profile, such as a Solana wallet address. You can check which account was used to authorize the login session using the getAuthorizationAccount() method.

```
// In the login handler
const authorization = await uauth.loginWithPopup();
const account = uauth.getAuthorizationAccount(authorization);

```

---
### Step 3: Verify the Login Flow and Scopes

<div class="flex justify-center">
<img src="/images/step3.png" style="width: 40vw;" />
</div>

- Modal 1. User clicks on Login with Unstoppable Button.
- Modal 2. A modal is displayed which allows the user to begin the authorization process by entering their Unstoppable domain.
- Modal 3. During login, the user will see the resolved address and the information being requested by the application (i.e. the scopes). The user must sign the transaction using their wallet address in order to share their information with the dApp.

---

### Step 4: Create Login Buttons

<div class="flex justify-center">
<img src="/images/button_style.png" style="width: 40vw;" />
</div>


---
### 4: Promote Your Application

<div class="flex justify-center">
<img src="/images/app_store.png" style="width: 40vw;" />
</div>

---

### Humanity Check for Login

To offer the Humanity Check feature, Unstoppable Domains has partnered with identity verification services such as Persona. When a Humanity Check provider verifies a new person, it assigns that person a new randomly generated ID number, which is then passed to UD.

#### Persona
Persona asks users to take a photo of their government-issued ID and a few selfies. Persona uses these images to verify that a person is who they claim to be. Every time Persona verifies a new person, it gives that person a new randomly generated ID number.

<div class="flex justify-center">
<img src="/images/humanity.png" style="width: 40vw;" />
</div>

---

### Scopes for Login

<div class="flex justify-center">
<img src="/images/login-scopes.png" style="width: 40vw;" />
</div>

Login with Unstoppable supports the following scopes which are detailed below:

```
openid (required)
wallet
email
humanity_check
profile
social
badges
```

---






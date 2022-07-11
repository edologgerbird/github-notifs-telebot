<!-- PROJECT LOGO -->
<div align="center">
  <a>
    <img src="images/banner.png" alt="Logo" height=150>
  </a>

  <h1 align="center">🤖 GitHub Telegram Notifications (GitHub Actions) 🤖 </h2>

  <p align="center">
    GitHub Actions for Telegram Bot Notifications
  </p>
</div>

<br/>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-the-project">About The Project</a></li>
    <li><a href="#getting-started">Getting Started<a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>
<br/>
<!-- ABOUT THE PROJECT -->

## About The Project

This project adds Telegram notification capabilities for GitHub Actions. By following the usage instructions, users can set-up notifications in their respective Telegram groups for notifications regarding GitHub Issues, Push commits, Pull requests and PR review comments.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

Getting started is easy and involves only 5 simple steps.

### Step 1: Creating a Telegram Bot with [@BotFather](https://t.me/BotFather)

1. Start a chat with [@BotFather](https://t.me/BotFather) on Telegram.
2. Create a new Telegram Bot with Telegram command `/newbot`.
3. Follow the prompts returned to name your new bot.
4. Upon successful creation of your new bot, you should recieve a token to access the bot via HTTP API.
   > Example Token: 123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
5. Add the new bot you have just created into the group you wish to receive notifications in.

> ❗ **Keep your token safe! Do not share or commit to public repositories! Use GitHub Secrets for safe storage and access.**

### Step 2: Retrieve Telegram Chat ID from the group you wish to receive notifications in

1. Identify which group you wish to receive notifications in.
2. To retrieve Group ID, add [@itpp_myid_bot](https://t.me/itpp_myid_bot) into your Telegram Group.
3. The [@itpp_myid_bot](https://t.me/itpp_myid_bot) bot should automatically send the Telegram User ID and Telegram Chat ID
4. The Telegram Chat ID is what we want. It is usually a negative integer.

> ❗ **Keep your Chat ID safe! Do not share or commit to public repositories! Use GitHub Secrets for safe storage and access.**

### Step 3: Inputing Telegram Tokens into your repository Secrets

1. Access your repository on [github.com](github.com).
2. Go to settings > Security > Secrets > Actions.
3. Create 2 new repository secrets - `TELEGRAM_TOKEN` and `TELEGRAM_CHAT_ID`.
4. Input the token from Step 1 and chat ID from Step 2 into the respective secrets.

### Step 4: Setting up GitHub Actions in your repository

1. Access your repository on [github.com](github.com).
2. Go to Actions > Workflows and click `New workflow`.
3. Define a new workflow by clicking `set up a workflow yourself`.
4. Delete the default template workflow.
5. Copy and paste the code block below into the YML file. If you would like to disable specific notification events, simply delete the respective event from the `on:` section.

```yml
name: telegram message notification
on:
  issues:
    types: [opened, reopened, deleted, closed]
  push:
  pull_request:
    types:
      [
        assigned,
        opened,
        closed,
        reopened,
        edited,
        review_requested,
        review_request_removed,
        ready_for_review,
      ]
  issue_comment:
  pull_request_review:
  pull_request_review_comment:

jobs:
  send-tele:
    uses: edologgerbird/github-notifs-telebot/.github/workflows/main.yml@main
    secrets:
      TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
      TELEGRAM_TOKEN: ${{ secrets.TELEGRAM_TOKEN }}
```

### Step 5: 🎉 Done! Enjoy your GitHub notifications! 🎉

Test your new GitHub workflow by pushing a commit to the repository.

<p align="right">(<a href="#top">back to top</a>)</p>
<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- LICENSE -->

## License

Distributed under the MIT License. See `LICENSE.md` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- CONTACT -->

## Contact

Edmund - edmund335@gmail.com

Project Link: [https://github.com/edologgerbird/github-notifs-telebot](https://github.com/edologgerbird/github-notifs-telebot)

<p align="right">(<a href="#top">back to top</a>)</p>

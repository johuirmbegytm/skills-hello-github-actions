<header>

# Hello GitHub Actions

_Create and run a GitHub Actions workflow._

</header>

## Finish

_Congratulations friend, you've completed this course!_

<img src=https://octodex.github.com/images/jetpacktocat.png alt="Mona the Octocat wearing a jetpack and smiling." width=300 align=right>

Here's a recap of all the tasks you've accomplished in your repository:

- You've created your first GitHub Actions workflow file.
- You learned where to make your workflow file.
- You defined an event trigger, a job, and a step for your workflow.
- You're ready to automate anything you can dream of.

### What's next?

- Learn more about GitHub Actions by reading "[Learn GitHub Actions](https://docs.github.com/actions/learn-github-actions)"
- Use actions created by others in [awesome-actions](https://github.com/sdras/awesome-actions)
- We'd love to hear what you thought of this course [in our discussion board](https://github.com/orgs/skills/discussions/categories/hello-github-actions)
- [Take another course on GitHub Actions](https://skills.github.com/#automate-workflows-with-github-actions)
- Learn more about GitHub by reading the "[Get started](https://docs.github.com/get-started)" docs
- To find projects to contribute to, check out [GitHub Explore](https://github.com/explore)

<footer>

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/hello-github-actions) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>

# Лабораторна-практична робота №10

## Тема:

Створення та запуск GitHub Actions workflow

## Мета:

Навчитися створювати файли робочих процесів (workflows) у GitHub Actions, налаштовувати тригери, завдання та кроки для автоматизації дій у репозиторії.

### Хід роботи:

#### 1.	Підготовка репозиторію

Для початку роботи було створено новий публічний репозиторій на основі навчального шаблону `skills/hello-github-actions.`

>![placeholder](https://github.com/johuirmbegytm/skills-hello-github-actions/blob/main/images/1.png?raw=true)

#### 2.	Створення файлу робочого процесу (Step 1-3)

Згідно з інструкціями курсу, у гілці `welcome-workflow` було створено файл конфігурації .`github/workflows/welcome.yml`. Цей файл описує автоматизацію, яка спрацьовує при відкритті нового `Pull Request`.

Вміст файлу `welcome.yml`:

```bash
name: Post welcome comment
on:
  pull_request:
    types: [opened]
permissions:
  pull-requests: write
jobs:
  build:
    name: Post welcome comment
    runs-on: ubuntu-latest
    steps:
      - run: gh pr comment $PR_URL --body "Welcome to the repository!"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          PR_URL: ${{ github.event.pull_request.html_url }}
```

#### 3.	Злиття змін (Step 4)

Після успішної перевірки створеного `workflow-файлу` було виконано злиття (`merge`) гілки `welcome-workflow` в основну гілку `main`. Це зробило автоматизацію активною для всього репозиторію.

#### 4.	Перевірка роботи автоматизації (Step 5)

Для тестування фінального результату було виконано наступні дії:
Створюємо нову гілку `test-workflow`.

>![placeholder](https://github.com/johuirmbegytm/skills-hello-github-actions/blob/main/images/2.png?raw=true)

Вносимо зміни у файл `README.md` (додано емодзі `🎉`).

>![placeholder](https://github.com/johuirmbegytm/skills-hello-github-actions/blob/main/images/3.png?raw=true)

Відкрито новий `Pull Request` до гілки `main`.

GitHub Actions автоматично виявив новий `Pull Request` і запустив створений нами скрипт. Бот `github-actions` миттєво залишив коментар "Welcome to the repository!" у обговоренні запиту.

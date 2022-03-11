<h1 align="center">Student of UCODE IT Academy
    <p> </p>
    <p align="center">
        <a href="https://ucode.world/en/" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/UCODE/ucode.png" height="60px">
        </a>
        <a href="https://lms.khpi.ucode-connect.study/login" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/UCODE/lms.png" height="60px">
        </a>
    </p>
</h1>

<h3 align="center">Language skills:</h3>
<p align="center">
    <a href="https://en.wikipedia.org/wiki/Russian_language" target="_blank"><img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/language/ru.png" width="15"/></a><b> Russian </b>— C1<br>
    <a href="https://en.wikipedia.org/wiki/Ukrainian_language" target="_blank"><img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/language/ua.png" width="15"/></a><b> Ukrainian </b>— B1<br>
    <a href="https://en.wikipedia.org/wiki/English_language" target="_blank"><img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/language/ang.png" width="15"/></a><b> English </b>— С1<br>
</p>
<h2> </h2>

<h2 align="center">Social Network:
    <p> </p>
    <p align="center">
        <a href="#" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/social_network/discord.png" height="40px">
        </a>
        <a href="https://t.me/Camyrau_B_Tanke" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/social_network/telegram.png" height="40px">
        </a>
        <a href="https://www.instagram.com/Camyrau_B_Tanke/" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/social_network/instagram.png" height="40px">
        </a>
        <a href="mailto:gunko.vlad.21.09.2001a@gmail.com" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/social_network/gmail.png" height="40px">
        </a>
        <a href="https://www.youtube.com/channel/UCCIaTyFJqvO1SanxoltkOAA" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/social_network/youtube.png" height="40px">
        </a>
    </p>
</h2>

<h2 align="center">Skills:
    <p> </p>
    <p align="center">
        <a href="https://ucode.world/en/" target="_blank">
            <img src="https://github.com/CamyrauBTanke/CamyrauBTanke/blob/main/img/UCODE/ucode.png" height="60px">
        </a>
    </p>
</h2>

# Contribution guide for [@mondeja][mondeja-link]'s Python projects

I always use the same conventions:

- Dependencies grouped using
 [setuptools' `extras_require` option][setuptools-options].
- [`pytest`][pytest-link] for testing.
- Checking and linting tasks defined in a [`pre-commit`][pre-commit-link]
 `.pre-commit-config.yaml` file.
- Usage of [`repo-stream`][repo-stream-link] and
 [Github Actions workflows][gh-actions-workflows] to perform certain periodic
 tasks.

## Development installation

First, create a fork of the project under your username using Github UI.
After that you can clone the project and setup for development.

```bash
$ git clone https://github.com/<your-username>/<project>.git
$ cd <project>
$ python3 -m vitualenv venv
$ . venv/bin/activate
(venv) $ python3 -m pip install -e .[dev]
(venv) $ pre-commit install
```

I define `dev` as a group which defines all other dependencies for
documentation, testing and linting. These have their correspondient groups as
well being `tests`, `lint` and `docs`.

Maybe you only want to install the testing dependencies. In such case use:

```bash
(venv) $ python3 -m pip install -e .[tests]
```

## Contribution workflow

Add a GIT remote for retrieve new changes from main master:

```bash
$ git add remote upstream https://github.com/mondeja/<project>.git
```

Retrieve the latest changes in master:

```bash
$ git checkout master
$ git fetch upstream
$ git merge upstream/master
```

Create a branch for the new feature of bug fix in which you are going to work:

```bash
$ git checkout -b <feature-or-bugfix>
```

Make changes to the project and then send them to your fork in Github:

```bash
$ git add path/to/changed/file.ext
$ git commit -m "I've changed foo and bar"
$ git push origin <feature-or-bugfix>
```

> When you run `git commit`, the [`pre-commit`][pre-commit-link] hooks will
 be executed and, if your changes are not allowed by the configuration, the
 commit will not be done, so you must make the required changes and run
 `git add ...` and `git commit` again.

You'll see a link for opening a pull request using the Github UI.

## Tests execution

```bash
(venv) $ python3 -m pytest -s
```

## Documentation building

I ussually create documentation in three forms:

### `README.md`

For small projects, the documentation and reference are in the `README.md`
file, optionally translated by a [`md2po2md`][md2po2md-pc-hook] hook in the
`.pre-commit-config.yaml` file.

Use `pre-commit run -a` for translate the README if the translation is
configured.

### [Mkdocs][mkdocs-link]

If you see a `mkdocs.yml` file at the root of the project, is documented
using [Mkdocs][mkdocs-link] in a folder named `docs`, optionally translated
by [`mkdocs-mdpo-plugin`][mkdocs-mdpo-plugin-link].

To build the documentation:

```bash
(venv) $ python3 -m mkdocs build
```

### [Sphinx][sphinx-link]

If there is no `mkdocs.yml` and there is a `docs` folder with `.rst` files,
the project is translated using [Sphinx][sphinx-link] and
[Readthedocs][readthedocs-link].

Use next command to fully rebuild the documentation from the root of the
project

```bash
(venv) $ python3 -m sphinx -T -E \
  -b html \
  -d docs/_build/doctrees \
  -D language=en \
  docs docs/_build/html
```

or just

```bash
cd docs && make html; cd ..
```

[mondeja-link]: https://github.com/mondeja
[pytest-link]: https://docs.pytest.org
[pre-commit-link]: https://pre-commit.com
[setuptools-options]: https://setuptools.readthedocs.io/en/latest/userguide/declarative_config.html?highlight=options.extras_require#options
[repo-stream-link]: https://github.com/mondeja/repo-stream
[gh-actions-workflows]: https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions
[md2po2md-pc-hook]: https://mdpo.readthedocs.io/en/master/pre-commit-hooks.html#md2po2md
[mkdocs-link]: https://mkdocs.org
[mkdocs-mdpo-plugin-link]: https://mkdocs-mdpo.ga
[sphinx-link]: https://www.sphinx-doc.org
[readthedocs-link]: https://readthedocs.org

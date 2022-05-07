# 2022-05-06T18:00:00-07:00

## Agenda

* Decided to "fix" the PowerShell venv script:
  * https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies
  * `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
  * The above seems safe enough - would recommend reading docs before using
* Fixing the wheel to include dependencies
  * `pip install wheel`
  * `./setup.py bdist_wheel`
    * Now unsure of whether we needed the above steps
  * https://packaging.python.org/en/latest/discussions/install-requires-vs-requirements/
  * Need to add `install_requires` to `setup.py`
* Now it works!
  * From GitHub action download `dist.zip`
  * Unzip `pinbot9000-1.0-py3-none-any.whl`
  * Run `pip install --force-reinstall .\pinbot9000-1.0-py3-none-any.whl`
  * `.venv\lib\site-packages\main.py`
* Load bot credentials from somewhere else
  * Avoid command line - readable by other processes
  * Environment variable?

## Stream questions

* Better to catch OSError on missing file or performing some sort of test?

## Resources from chat

* Online ML Book: https://d2l.ai/chapter_preface/index.html

## More stream ideas

* Include GitHub build number in wheel package version

You can build and check the created website in a local computer using the below command.

```bash
make html && google-chrome _build/html/index.html
```
(If you don't want a new tab every time, you can just ```make html``` and refresh)

---

For first runs, you need ```sphinx``` and its related libraries.
run:
```bash
pip install sphinx sphinx_design sphinxcontrib-video sphinxcontrib-youtube sphinx_rtd_theme
```
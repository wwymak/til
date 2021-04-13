# Removing code cells from jupyter export

Sometimes, it is useful to remove code cells from a jupyter notebook, e.g. when you are exporting it as  report to 
non tech people. The quick and easy way to do it is to run in terminal:

```bash
jupyter nbconvert path/to/your/ipynb --to=pdf --TemplateExporter.exclude_input=True
```

(courtesy of https://stackoverflow.com/a/54610579/11956075)

→ To Install Globally via npm type: 

```bash
npm install -g @qwen-code/qwen-code@latest
```


→ To Know the Latest Published version on npm and your installed version type: 

```bash
npm show @qwen-code/qwen-code version
qwen --version
```

### How to Allow Qwen Code to Read and Write from External Directories

→ Got to this directory: 
/Users/ahmed/.qwen/settings.json
and adjust the json file as follows: 

```json
{
  "selectedAuthType": "qwen-oauth",
  "includeDirectories": [
    "/Volumes/Samsung T5/Odoo/Odoo/odoo-18/Odoo 18 Community/",
    "/Volumes/Samsung T5/Odoo/Odoo/odoo-18/enterprise/",
    "/Users/ahmed/Documents/",
    "/Volumes/Samsung T5/Odoo/Development & Study/odoo-18.0/",
    "/Volumes/Samsung T5/Odoo/Development & Study/odoo-18.0/enterprise/"
  ]
}
```

→ Refer to this link for more: 
https://www.zdoc.app/en/QwenLM/qwen-code/blob/main/docs/cli/configuration.md

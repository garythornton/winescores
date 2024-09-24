<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Password Protected</title>

        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta name="robots" content="noindex, nofollow">

        <style>
            *,
            *:after,
            *:before {
                box-sizing: border-box;
            }
            body,
            html {
                font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
                font-weight: 300;
                font-size: 16px;
                background: #f2f2f2;
                color: #2D3737;
                display: flex;
                align-items: center;
                justify-content: center;
                min-height: 100%;
            }

            .protected {
                background: #fff;
                -webkit-box-shadow: 0 2px 3px 0 rgba(0,0,0,0.1);
                box-shadow: 0 2px 3px 0 rgba(0,0,0,0.1);
                border-radius: 3px;
                min-width: 500px;

            }
            .protected__content {
                padding: 24px 28px;
            }
            .protected__content__heading {
                font-size: 16px;
                font-weight: 500;
                margin: 0 0 12px;
                line-height: 1;
            }
            .protected__alert {
                display: none;
                border-bottom: 1px solid transparent;
                border-radius: 3px 3px 0 0;
                padding: 12px 14px;
                color: #a94442;
                background-color: #f2dede;
                border-color: #ebccd1;
            }
            .protected__content__input {
                display: block;
                border: solid 1px #ccc;
                padding: 12px 14px;
                -webkit-box-shadow: 0 2px 3px 0 rgba(0,0,0,0.1);
                box-shadow: 0 2px 3px 0 rgba(0,0,0,0.1);
                font-size: 16px;
                width: 100%;
                border-radius: 3px;

                margin-bottom: 12px;
            }
            .protected__content__input:focus {
                outline: none;
                border-color: #228843;
            }
            .protected__content__btn {
                background-color: #228843;
                border-radius: 3px;
                cursor: pointer;
                border: none;
                color: #fff;
                padding: 12px 14px;
                font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
                font-weight: 500;
                font-size: 16px;

            }
            .protected__content__btn:hover {
                background-color: #1C6D36;
            }

        </style>

    </head>

    <body>

        <div class="protected">
            <div class="protected__alert" data-id="alert">You entered the wrong password</div>
            <div class="protected__content">
                <h1 class="protected__content__heading">You need a password to continue</h1>
                <input class="protected__content__input" data-id="password" type="password" placeholder="password"/>
                <button data-id="button" type="button" class="protected__content__btn">Continue</button>
            </div>
        </div>

        <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/js-sha1/0.6.0/sha1.min.js"></script>
        <script type="text/javascript">
            "use strict"
            var button = document.querySelectorAll('[data-id="button"]')
            var password = document.querySelectorAll('[data-id="password"]')

            function login(secret) {
                var hash = sha1(secret)
                var url = hash + "/index.html"
                var alert = document.querySelectorAll('[data-id="alert"]')

                var request = new XMLHttpRequest()
                request.open('GET', url, true)

                request.onload = function () {
                    if (request.status >= 200 && request.status < 400) {
                        window.location = url
                    } else {
                        parent.location.hash = hash
                        alert[0].style.display = 'block'
                        password[0].setAttribute('placeholder', 'Incorrect password')
                        password[0].value = ''
                    }
                }
                request.onerror = function () {
                    parent.location.hash = hash
                    alert[0].style.display = 'block'
                    password[0].setAttribute('placeholder', 'Incorrect password')
                    password[0].value = ''
                }
                request.send()
            }

            button[0].addEventListener("click", function () {
                login(password[0].value)
            })

            document.onkeydown = function (e) {
                e = e || window.event
                if (e.keyCode == 13) {
                    login(password[0].value)
                }
            }
        </script>

<DIV>
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/garythornton/winescores/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/garythornton/winescores/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
</DIV>
        
    </body>
</html>





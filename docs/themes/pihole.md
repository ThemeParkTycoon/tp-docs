<h1 align="center"> <img src="/site_assets/{{ page.title.split()[0].lower() }}/logo.png" alt="logo" width="30" height="30"> {{ page.title.split()[0] }}</h1>

Custom [{{ page.title.split()[0] }}](https://github.com/pi-hole/pi-hole) CSS

<p align="center"> Aquamarine Theme </p>

![](/site_assets/{{ page.title.split()[0].lower() }}/aquamarine.png)


## 🛠️ Installation

### [Setup](/setup)

!!! note
    Tested on Web Interface v5.5
     Set theme to dark in the Web  interface menu.

!!! warning "Subfilter CSP"
    Because Pi-hole uses CSP it will block any attempts to inject stylesheets.
    This will add `https://raw.githubusercontent.com` and `https://theme-park.dev` to the CSP meta tag in the HTML. Allowing you to load the custom css.

```nginx
proxy_set_header Accept-Encoding "";
sub_filter
'</head>'
'<link rel="stylesheet" type="text/css" href="https://theme-park.dev/css/base/pihole/<THEME>.css">
</head>';
sub_filter_once on;
proxy_hide_header Content-Security-Policy;
add_header Content-Security-Policy "default-src 'none'; base-uri 'none'; child-src 'self'; form-action 'self'; frame-src 'self'; font-src 'self'; connect-src 'self'; img-src 'self' https://raw.githubusercontent.com; manifest-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' https://raw.githubusercontent.com https://theme-park.dev 'unsafe-inline'";
```

{% set addons = extra.addons %}
{% set title = page.title.split()[0].lower() %}
{% for app, addon_name in addons.items() %}
    {% if app  ==  title %}

### Addons

        {% for el in addon_name.items() %}
            {% set name =  el[0]  %}
            {% for p in el[1].items() %}
            {% set path = p[1] %}

### [{{ name }}](/{{ path }})

            {% endfor %}
        {% endfor %}
    {% endif %}
{% endfor %}

## Screenshots

{% set themes = config.extra.themes %}
{% for theme in themes %}
<p align="center">  
<a href="/site_assets/{{ page.title.split()[0].lower() }}/{{ theme }}.png">{{ theme.capitalize() }} Theme<img src="/site_assets/{{ page.title.split()[0].lower() }}/{{ theme }}.png"></img>
</p>
{% endfor %}

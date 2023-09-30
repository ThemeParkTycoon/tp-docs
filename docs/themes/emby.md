<h1 align="center"> <img src="/site_assets/{{ page.title.split()[0].lower() }}/logo.png" alt="logo" width="30" height="30"> {{ page.title.split()[0] }}</h1>

Custom [{{ page.title.split()[0] }}](https://github.com/MediaBrowser/Emby) CSS

<p align="center"> Organizr Dark Theme </p>

![](/site_assets/{{ page.title.split()[0].lower() }}/organizr.png)

## 🛠️ Installation

### Docker Mod

!!! note  "Docker Mod 🐳"
    Set the theme to `Light` as the [mod](https://github.com/themepark-dev/theme.park/blob/master/docker-mods/{{ page.title.split()[0].lower() }}/root/etc/cont-init.d/98-themepark) changes the `/dashboard-ui/modules/themes/light/theme.css` file

### Subfilter

!!! warning Subfiltering
    Subfiltering can make your Emby instance unavailable remotely. Seems like they have some security features, or something breaks when changing the HTML.

    You need to subfilter the `</body>` instead of the `</head>` tag. See example below.

```nginx
proxy_set_header Accept-Encoding "";
sub_filter
'</body>'
'<link rel="stylesheet" type="text/css" href="https://theme-park.dev/css/base/emby/dracula.css">
</body>';
sub_filter_once on;
```

### [Setup](/setup)

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

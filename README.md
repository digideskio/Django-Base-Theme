### Django Base Theme
- A responsive front-end boilerplate designed for <a href="http://wharton.upenn.edu">Wharton</a> <a href="https://www.djangoproject.com">Django</a>/<a href="https://www.python.org">Python</a> apps.
- It contains helpful plugins, components and standards to help you get started.
- It includes <a href="http://standards.wharton.upenn.edu">official Wharton branding styles, logos, layouts and fonts</a>.

### Table of Contents
- Components & Standards
- CSS Guidelines & Architecture
- Browser Support
- Performance
- SASS/SCSS Integration
- Using Gulp to automate your front-end workflow
- Modifying Settings.py
	- Adding Directories
	- Adding Installed Apps
- PIP installation
- Updating Base-Theme
- Adding custom stylesheets/javascript
- Custom templates and other static files
	- Example directory structure
	- Example of base.html file
	- Example of extending your app's base file
	- Examples of different template layout options
- Utilizing the Django Block System
	- A list of blocks available with base-theme
- Adding Django Debug Toolbar
- Example View & URL Dispatcher
- List of Contributors
	
### Components & Standards: 

- <a href="http://getbootstrap.com">Twitter Bootstrap 3</a>
- <a href="http://necolas.github.io/normalize.css">Normalize Reset</a>
- <a href="https://html5boilerplate.com">HTML5 Boilerplate</a>
- HTML5 & CSS3
- Responsive
- <a href="https://smacss.com/">SMACSS Architecture</a>
- <a href="http://cssguidelin.es/">cssguidelin.es</a> by <a href="http://csswizardry.com/work">Harry Roberts</a>
- <a href="http://sass-lang.com">SASS/SCSS</a>
- <a href="https://jquery.com">jQuery</a>
- <a href="http://modernizr.com">Modernizer.js</a>
- <a href="http://fortawesome.github.io/Font-Awesome">Font Awesome</a>
- <a href="http://www.fonts.com">Custom fonts served via Fonts.com</a>
- <a href="http://gulpjs.com">Gulp Workflow Automation</a>

### CSS Guidelines & Architecture
We use the following guides: 

- <a href="https://smacss.com/">SMACSS Architecture</a>
- <a href="http://cssguidelin.es/">cssguidelin.es</a> by <a href="http://csswizardry.com/work">Harry Roberts</a>

### Browser Support
At present, we officially aim to support the following browsers:

- IE10, IE11, MS Edge
- The latest version of Chrome, Firefox, Safari & Opera
- The latest version of Safari & Chrome for iOS
- The latest version of Chrome for Android
- Find out if you are using the most up-to-date browser at <a href="http://whatbrowser.org">http://whatbrowser.org</a> or <a href="http://browsehappy.com">http://browsehappy.com</a>.

This is not to say that Django Base Theme cannot be used in browsers older than those reflected, but that the best experience and our development focus will be on those browsers listed above.

### Performance

Base Theme strives for fast page load times. Not including server configuration enhancements, Base Theme's default template scores a grade of "A" in every category via <a href="http://yslow.org">YSlow's</a> web page analyzer. Our median <a href="http://www.webpagetest.org">Web Page Test</a> scores for the default template have a Speed Index of ~1450 (we are working on getting it down to ~1000, which is ideal).

### SASS/SCSS Integration

This project uses the CSS extension language <a href="http://sass-lang.com">SASS</a>. SASS adds power and organization to your stylesheets.

SCSS/SASS outputs to CSS via compilers like <a href="http://compass-style.org">Compass</a>, <a href="http://libsass.org">LibSass</a>, <a href="https://incident57.com/codekit">CodeKit</a> or <a href="http://gulpjs.com">Gulp</a>.<a href="http://sass-lang.com"> Learn more about SASS/SCSS</a>. 

Some helpful SASS Mixins included in this theme are:

- Flexbox
- Breakpoints
- REM to PX fallback & Viewport to REM to PX fallback
- SVG Background-images with PNG and retina fallBack
- RGBA Background, Vertical Align, Horizontal Align, etc.
- You can see a full list of mixins, variables and other SASS helpers <a href="https://github.com/chadwhitman/django-base-theme/tree/master/base_theme/static/base_theme/scss/scss/helpers/_functions.scss">here</a>.

### Using Gulp to automate your front-end workflow 

Included in this repo is an <a href="https://github.com/chadwhitman/django-base-theme/blob/master/base_theme/static/base_theme/gulpfile.js">example gulpfile</a> (based on: <a href='http://www.revsys.com/blog/2014/oct/21/ultimate-front-end-development-setup/'>RevSys' Front-end Guide</a>). If you use Gulp, you will need to manually add it to your root directory and customize it to your project's needs. For more info on how to use Gulp go here: <a href="http://gulpjs.com">http://gulpjs.com</a>.

### Modifying Settings.py

#### Add the following to your settings.py file:

<pre><code>STATIC_ROOT = os.path.join(BASE_DIR, "static")

STATICFILES_DIRS = (
    os.path.join(BASE_DIR, "static_dev"), 
    #### You can also call this assets or whatever name you want
)
</code></pre>

<pre><code>TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'], #### template directory goes here
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]</code></pre>

#### Add the following to the 'Installed_Apps' section: 

<pre><code>'bootstrap3',
'base_theme',
'fontawesome',
</code></pre>

### PIP installation

<pre><code>pip install git+https://github.com/chadwhitman/Django-Base-Theme</code></pre>
	
<pre><code>pip install django-bootstrap3</code></pre>

<pre><code>pip install django-fontawesome</code></pre>

### Getting the latest Base-Theme Updates

To get the latest updates to the base theme, just run the following command: 

<pre><code>pip install git+https://github.com/chadwhitman/Django-Base-Theme --upgrade</code></pre>

### Add custom stylesheets or javascript

1.) Create a new folder in your project directory called "assets." You can also call this "static_dev" or whatever name you want.

2.) Create your custom stylesheets and/or javascript files in the assets folder.

3.) Include a link to your custom styles/js. <a href="https://github.com/chadwhitman/django-base-theme/blob/master/base_theme/templates/your_app/base.html">Here is an example</a>.
    
### Custom templates and other static files:

1.) Create a new folder in your project directory called "templates."
		
2.) Create a directory within "templates" for your app and call it the name of your app. 
    So, if your app is "polls," your folder would be called "polls."

3.) Within that app folder, create a template called "base.html." You must have this file in your app directory.

4.) Example directory structure:

<pre><code>project/
		manage.py
project/
		settings.py
		urls.py
your-app/
		models.py
		views.py
assets/
		 styles.css #### Your custom styles here.
		 scripts.js #### Your custom js here.
templates/
     your-app/ #### same name as your app
           base.html #### Your base extends one of the layout templates.
           	i.e. {% extends "left_sidebar.html" %}
           list.html #### Your other templates can extend from your app's base template
           	i.e. {% extends "your-app/base.html" %}
           detail.html
</code></pre>

5.) Note: The layouts (left, right, both, full) extend the original base.html.
		The original base.html will be in your site-packages directory after you pip install it.

6.) <a href="https://github.com/chadwhitman/django-base-theme/blob/master/base_theme/templates/your_app/base.html">Here is an example of what would go into your app's base.html</a>.
    
7.) If you wanted to extend your app's base.html into, say, your app's list.html template, you would just need to make sure your extends path is pointing to your app's base template, like this:

<pre><code>{% extends "your-app/base.html" %}</code></pre>
    
8.) You can find different layouts for your app <a href="https://github.com/chadwhitman/django-base-theme/tree/master/base_theme/templates">here</a>.  
           
### Utilizing the Django Block System

The <a href="https://docs.djangoproject.com/en/1.8/topics/templates/#template-inheritance">official Django docs</a> do a good job of explaining how template inheritance works and how to utilize the block system.

The following is a list of blocks included in the Django Base Theme that you can use to customize your own template as needed. You can also find them listed in the original base.html template <a href="https://github.com/chadwhitman/django-base-theme/blob/master/base_theme/templates/base.html">here</a>. 

<pre><code>- {% block site_title %} 
- {% block extra_head_top %}
- {% block fast_fonts %}
- {% block head_css %}
- {% block font_awesome %}
- {% block extra_head_bottom %}
- {% block header_wrapper %}
- {% block header %}
- {% block banner_wrapper %}
- {% block banner_logo %}
- {% block banner_title %}
- {% block main_nav_wrapper %}
- {% block main_nav %}
- {% block mobile_sidebar_nav %}
- {% block breadcrumb_wrapper %}
- {% block breadcrumb %}
- {% block content_wrapper %}
- {% block content %}
- {% block inner_content %}
- {% block left_sidebar %}
- {% block right_sidebar %}
- {% block footer_wrapper %}
- {% block footer %}
- {% block footer_app_link %}
- {% block footer_js %}
- {% block extra_footer_js %}
</code></pre>

### Adding the Django Debug Toolbar

The <a href="http://django-debug-toolbar.readthedocs.org/en/latest/installation.html">official Django docs</a> do a good job of explaining how to integrate the toolbar.

### Initial Test View & Url Configuration

#### And to your views

<pre><code>from django.views.generic import TemplateView

class BaseView(TemplateView):
    template_name = "your_app/base.html" 
</code></pre>
    
#### URL Dispatcher

<pre><code>from project.views import BaseView
urlpatterns = [
    url(r'^$', BaseView.as_view(), name='home'),
    url(r'^admin/', include(admin.site.urls)),
]
</code></pre>

### Contributors

Thank you to our contributors!

* Chad Whitman <a href="https://github.com/chadwhitman">https://github.com/chadwhitman</a>
* Tim Allen <a href="https://github.com/flipperpa">https://github.com/flipperpa</a>
* Frank Wiles <a href="https://github.com/frankwiles">https://github.com/frankwiles</a>

# ckanext-google_tag_manager

This is a CKAN extension (plugin) which enables 'Google Tag Manager' for your CKAN instance. 

### Pre-requisites
Create account for you CKAN instance with [Google Tag Manager].
This gives you a container-ID specific to the account. 

### Installation
##### 1. Get the code
    
```sh 
$ cd /usr/lib/ckan/default/src
$ git clone https://github.com/tanmaythakur/ckanext-google-tag-manager.git
```

##### 2. Install the plugin

```sh
# Activate virtual env 
$ . /usr/lib/ckan/default/bin/activate
$ cd ckanext-google-tag-manager
$ pip install -r requirements.txt
$ python setup.py develop
```

##### 3. Make config changes

- Open your development.ini file (/etc/ckan/default/development.ini).
- Add `ckan.google_tag_manager.gtm_container_id = {YOUR_CONTAINER_ID}` anywhere in the `[app:main]` section.
- Add the extension to the plugins list:
    ` ckan.plugins = google_tag_manager`


##### 4. Restart ckan

```bash
    paster serve --reload /etc/ckan/default/development.ini
```

### Common Errors

* ##### GET http://www.googletagmanager.com/gtm.js?id=False 404 (Not Found)

    This error is seen in console of a web browser, when `ckan.google_tag_manager.gtm_container_id` is not specified in the config file (development.ini or production.ini)

* ##### GET http://www.googletagmanager.com/gtm.js?id=GTM-xxxxx  

    This error is seen in console of a web browser, if either the container-ID GTM-xxxxx (in this case) is invalid or the account is not published from [Google Tag Manager]. 
    

### Future and Contribution Guide

The plugin is still in development phase. I plan to keep the `master` branch with the most recent stable codebase and `dev` branch with latest development branch. Please help me to improve the code by contributing to the `dev` branch. 
##### ToDo:
- Add warning log if `ckan.google_tag_manager.gtm_container_id` is not specified in config file.
- Beautify the README.md file.


[Google Tag Manager]: https://tagmanager.google.com/?hl=en#/home


### 配置Apache

apache、php和phpMyAdmin的根目录分别为：“D:\Apache24"、“D:\php7"、“D:/phpMyAdmin”，更改“D:\Apache24\conf”下“httpd.conf"文件,加粗部分为增加部分；

`#Dynamic Shared Object (DSO) Support`

`#To be able to use the functionality of a module which was built as a DSO you`

`#have to place corresponding `LoadModule' lines at this location so the`

`#directives contained in it are actually available _before_ they are used.`

`#Statically compiled modules (those listed by `httpd -l') do not need`

`#to be loaded here.`

`#`

`#Example:`

`#LoadModule foo_module modules/mod_foo.so`

`#`
`#LoadFile "D:\php7\php5ts.dll"`
**`LoadModule php7_module "D:\php7\php7apache2_4.dll"`**
**`PHPIniDir "D:\php7"`**
`LoadModule access_compat_module modules/mod_access_compat.so`
`LoadModule actions_module modules/mod_actions.so`
`LoadModule alias_module modules/mod_alias.so`

`.....`

**`<IfModule dir_module>`**
​    **`DirectoryIndex index.php index.html`**
**`</IfModule>`**

......

`#Various default settings`

`#Include conf/extra/httpd-default.conf`
**`Include conf/phpmyadmin.conf`**

`#Configure mod_proxy_html to understand HTML4/XHTML1`

`<IfModule proxy_html_module>`
`Include conf/extra/proxy-html.conf`

`</IfModule>`

在conf文件夹下新建文件phpmyadmin.conf，其内容为：

`Alias /phpmyadmin "D:/phpMyAdmin"`
`<Directory "D:/phpMyAdmin">`
`Options Indexes FollowSymLinks MultiViews`
`AllowOverride all`
`Require all granted`
`php_admin_value upload_max_filesize 128M`
`php_admin_value post_max_size 128M`
`php_admin_value max_execution_time 360`
`php_admin_value max_input_time 360`
`</Directory>`

从新启动Apache

### 配置php

在php根目录下（“D:\php7”）打开php.ini文件，黑色部分为添加内容：

`; Directory in which the loadable extensions (modules) reside.`
`; http://php.net/extension-dir`
`; extension_dir = "./"`
`; On windows:`
`; extension_dir = "ext"`
**`extension_dir = "D:\php7\ext"`**
**`extension=php_mysqli.dll`**
`; Directory where the temporary files should be placed.`
`; Defaults to the system default (see sys_get_temp_dir)`
`; sys_temp_dir = "/tmp"`

### 配置phpMyAdmin

修改“D:\phpMyAdmin\libraries”下的config.default.php

`/**`

`*The 'cookie' auth_type uses AES algorithm to encrypt the password. If`

`*at least one server configuration uses 'cookie' auth_type, enter here a`

`*pass phrase that will be used by AES. The maximum length seems to be 46`

`*characters.`
`*`

`*@global string $cfg['blowfish_secret']`
`*/`
**`$cfg['blowfish_secret'] ='578629fc5d1de07d685e2eb8e01edb0e730afd460567d4b5da25f59ba77eec17';`**

`......`

`*MySQL user`
`*`

`*@global string $cfg['Servers'][$i]['user']`
`*/`
**`$cfg['Servers'][$i]['user'] = 'root';`**

`/**`

`*MySQL password (only needed with 'config' auth_type)`
`*`

`*@global string $cfg['Servers'][$i]['password']`
`*/`
**`$cfg['Servers'][$i]['password'] = 'yang948418';`**

修改“D:\phpMyAdmin\”下的config.inc.php

**``$cfg['Servers'][$i]['controluser'] = 'root';`**
 **$cfg['Servers'][$i]['controlpass'] = 'yang948418';`**
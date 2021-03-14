# 使用Apache2.4运行python3 Django

系统版本

CentOS Linux release 7.8.2003 (Core)

python 3.6 yum安装

## 环境安装

python3.6-dev一定要有，推荐一键安装依赖

requirements

## 在Apache安装插件mod_wsgi

```shell
wget https://github.com/GrahamDumpleton/mod_wsgi/archive/4.7.1.zip

cd mod_wsgi-4.7.1
```

在配置时就关联上apache apxs和python，再进行make

```shell
./configure --with-apxs=/usr/local/http-2.4.46/bin/apxs --with-python=/usr/bin/python3.6

make && make install
```

## 安装配置Apache2.4

进入apache的conf文件夹

vim httpd.conf

```xml
# Distributed authoring and versioning (WebDAV)
#Include conf/extra/httpd-dav.conf

# Various default settings
#Include conf/extra/httpd-default.conf

# Configure mod_proxy_html to understand HTML4/XHTML1
<IfModule proxy_html_module>
Include conf/extra/proxy-html.conf
</IfModule>

# Secure (SSL/TLS) connections
#Include conf/extra/httpd-ssl.conf
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>

```

vim ./extra/httpd-vhosts.conf

```xml
<VirtualHost *:80>
    ServerName sc3
    ServerAdmin xx@xx.com

    DocumentRoot "/usr/dev/sc3"
    WSGIScriptAlias / "/usr/dev/sc3/sc3/wsgi.py"

    <Directory "/usr/dev/sc3">
        Require all granted
    </Directory>

    Alias /media "/usr/dev/sc3/media"
    Alias /static "/usr/dev/sc3/sc3/collectedstatic"

    <Directory "/usr/dev/sc3/sc3/collectedstatic">
        Require all granted
    </Directory>

    <Directory "/usr/dev/sc3/sc3/media">
        Require all granted
    </Directory>
</VirtualHost>

```

在 /usr/dev/sc3/sc3/wsgi.py 内增加路径标识：

```python
import sys

sys.path.append('/usr/dev/sc3')
sys.path.append('/usr/dev/sc3/sc3')
```

进入bin重启即可

```shell
apachectl restart

```




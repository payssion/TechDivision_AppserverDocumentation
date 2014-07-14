#VirtualHostModule

Usage
-----------------
The module can be used according to the `\TechDivision\WebServer\Interfaces\ModuleInterface` interface.
It needs an initial call of the `init` method and will process any request offered to the `process` method.
The module is best used within the [`TechDivision_WebServer`](<https://github.com/techdivision/TechDivision_WebServer>)
project as it offers all needed infrastructure.

Examples
--------

The following examples should help you to configure your application with default settings usually
provided with the applications .htaccess files.

Magento:

```xml
<virtualHost name="magento-real-vhost.dev magento-real-vhost.local">
    <params>
        <param name="admin" type="string">info@appserver.io</param>
        <param name="documentRoot" type="string">webapps</param>
    </params>
    <rewrites>
        <rewrite condition="-d{OR}-f{OR}-l" target="" flag="L" />
        <rewrite condition="(.*)" target="index.php/$1" flag="L" />
    </rewrites>
    <accesses>
        <access type="allow">
            <params>
                <param name="X_REQUEST_URI" type="string">^\/([^\/]+\/)?(media|skin|js|index\.php).*
                </param>
            </params>
        </access>
    </accesses>
</virtualHost>
```

TYPO3 Neos

```xml
<virtualHost name="neos.local">
    <params>
        <param name="admin" type="string">info@appserver.io</param>
        <param name="documentRoot" type="string">webapps/neos-1.0.2/Web
        </param>
    </params>
    <rewrites>
        <rewrite
            condition="^/(_Resources/Packages/|robots\.txt|favicon\.ico){OR}-d{OR}-f{OR}-l"
            target="" flag="L" />
        <rewrite
            condition="^/(_Resources/Persistent/[a-z0-9]+/(.+/)?[a-f0-9]{40})/.+(\..+)"
            target="$1$3" flag="L" />
        <rewrite condition="^/(_Resources/Persistent/.{40})/.+(\..+)"
            target="$1$2" flag="L" />
        <rewrite condition="^/_Resources/.*" target="" flag="L" />
        <rewrite condition="(.*)" target="index.php" flag="L" />
    </rewrites>
    <environmentVariables>
        <environmentVariable condition=""
            definition="FLOW_REWRITEURLS=1" />
        <environmentVariable condition=""
            definition="FLOW_CONTEXT=Production" />
        <environmentVariable condition="Basic ([a-zA-Z0-9\+/=]+)@$Authorization"
            definition="REMOTE_AUTHORIZATION=$1" />
    </environmentVariables>
</virtualHost>
```

ORO CRM

```xml
<virtualHost name="oro-crm.local">
    <params>
        <param name="admin" type="string">info@appserver.io</param>
        <param name="documentRoot" type="string">webapps/crm-application/web
        </param>
    </params>
    <rewrites>
        <rewrite condition="%{REQUEST_FILENAME}" target="!-f"
            flag="" />
        <rewrite condition="^/(.*)$" target="app.php" flag="[QSA,L]" />
    </rewrites>
</virtualHost>
```

Wordpress

```xml
<virtualHost name="wordpress.local">
    <params>
        <param name="admin" type="string">info@appserver.io</param>
        <param name="documentRoot" type="string">webapps/wordpress</param>
    </params>
</virtualHost>
```

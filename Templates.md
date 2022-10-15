### Openshift Template

### Load new templates
`oc create -f ~/labs/build-template/php-mysql-ephemeral.json`

### uploading tempate in other project 
`oc create -f <filename> -n <project>`

### TO know about template params
`oc describe template php-mysql-ephemeral -n ${RHT_OCP4_DEV_USER}-common`

`oc process -f <filename> -l name=otherLabel`
### list parameters with the CLI 
 `oc process --parameters -f <filename>`
#### get objects as an template 
 `oc get -o yaml  is,bc,dc,svc,route > mytemplate.yaml`

`oc process -f mytemplate.yaml -p PARAM1=value1  -p PARAM2=value2 | oc create -f -`
`oc new-app --file mytemplate.yaml -p PARAM1=value1  -p PARAM2=value2`


The syntax available is not a full regular expression syntax. However, you can use \w, \d, \a, and \A modifiers:

[\w]{10} produces 10 alphabet characters, numbers, and underscores. This follows the PCRE standard and is equal to [a-zA-Z0-9_]{10}.
[\d]{10} produces 10 numbers. This is equal to [0-9]{10}.
[\a]{10} produces 10 alphabetical characters. This is equal to [a-zA-Z]{10}.
[\A]{10} produces 10 punctuation or symbol characters. This is equal to [~!@#$%\^&*()\-_+={}\[\]\\|<,>.?/"';:`]{10}.

 parameters:
  - name: PASSWORD
    description: "The random user password"
    generate: expression
    from: "[a-zA-Z0-9]{12}"

apiVersion: template.openshift.io/v1
kind: Template
metadata:
  name: quotes
  annotations:
    openshift.io/display-name: Quotes Application
    description: The Quotes application provides an HTTP API that returns a random, funny quote.
    iconClass: icon-php
    tags: php,mysql
objects:
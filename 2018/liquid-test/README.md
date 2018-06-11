# Liquid Templating Engine Test
This file is to test the best way to escape bracket pairs:.

**Char Entities:**

&#123;&#123; expression here &#125;&#125;


**Using Liquid Raw Tag:**

<% raw %> 
{{ stuff here}} 
<% endraw %>


## Shell Code Test

### Before

>![user input](../images/userinput.png)
>```shell
>FNSERVER_IP=$(docker inspect --type container -f '{{.NetworkSettings.IPAddress}}' fnserver)
>```

### After

>![user input](../images/userinput.png)
>```sh
>FNSERVER_IP=$(docker inspect --type container -f '{{.NetworkSettings.IPAddress}}' fnserver)
>```


### After 2

>![user input](../images/userinput.png)
>```shell
>FNSERVER_IP=$(docker inspect --type container -f &apos;&#123;&#123;.NetworkSettings.IPAddress&#125;&#125;&apos; fnserver)
>```




## Test Me
<https://michael-w-williams.github.io/demos/2018/liquid-test/>

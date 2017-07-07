# Tsuru Local Deploy
Local deploy with Tsuru


## Install

    tsuru plugin install local-deploy https://raw.githubusercontent.com/globocom/tsuru-local-deploy/master/local-deploy

## Usage
    # Usage: tsuru local-deploy start -a|--app <appname> [-p|--process <processname>] [-l|--local-folder <folderpath>] [-P|--port <port|8888>]
    # Usage: tsuru local-deploy update -a|--app <appname> [-p|--process <processname>] [-l|--local-folder <folderpath>] [-P|--port <port|8888>] [-c|--copy-environment]
    # Usage: tsuru local-deploy delete -a|--app <appname>
    tsuru local-deploy start -a TSURU_APP

## Example

Create your app from [example repo](https://github.com/globocom/local-deploy-test) with python platform on Tsuru:

    $ tsuru app-info -a local-deploy-test

    Units [web]: 1
    +--------------+---------+----------------+-------+
    | Unit         | State   | Host           | Port  |
    +--------------+---------+----------------+-------+
    | 51ceb4d449e8 | started | 10.131.225.176 | 32777 |
    +--------------+---------+----------------+-------+

    Units [worker]: 1
    +--------------+---------+----------------+-------+
    | Unit         | State   | Host           | Port  |
    +--------------+---------+----------------+-------+
    | c3fbd5acef44 | started | 10.131.225.176 | 32778 |
    +--------------+---------+----------------+-------+

    App Plan:
    +-------+-----------+------+-----------+---------+
    | Name  | Memory    | Swap | Cpu Share | Default |
    +-------+-----------+------+-----------+---------+
    | small | 268435456 | 0    | 1024      | false   |
    +-------+-----------+------+-----------+---------+

This project has 2 processes, a worker and a web server.

Start for the first time your application on local:

    tsuru local-deploy start -a local-deploy-test

Now you can edit environment variables that your local unit should use.

Then it should take a while because it's your first time...

At the end your app should be started at *http://localhost:8888*

You could change the port using:

    tsuru local-deploy start -a local-deploy-test -P 8080

Now it's fast and your app should be at *http://localhost:8080*

If you just want web server just choose your **Procfile** process by running:

    tsuru local-deploy start -a local-deploy-test -p web

Ok, let's develop with this. Just choose one local path to replace your project files using something like this:

    tsuru local-deploy start -a local-deploy-test -l ../workspace/local-deploy-test

Try to change your local files... Your process will restart automatically! It's magic!! Your app should be changed at *http://localhost:8888*

So, tsuru unit updated and your unit is not so good, than update it:

    tsuru local-deploy update -a local-deploy-test

It should take a while too... All your old environments will be intact and your unit is updated. If you want to get new environments again just use:

    tsuru local-deploy update -a local-deploy-test -c

Every **start** command arguments are supported by **update**.

Ok, I just don't need my deploy anymore... So:

    tsuru local-deploy delete -a local-deploy-test    
    

Enjoy!

Thank you [thor27](https://github.com/thor27) and [magnotorres](https://github.com/magnotorres) for your help
# Tsuru Local Deploy
Local deploy with Tsuru


## Install

    tsuru plugin install local-deploy https://raw.githubusercontent.com/globocom/tsuru-local-deploy/master/local-deploy

## Usage
    # Usage: tsuru local-deploy start -a|--app <appname> [-p|--process <processname>] [-l|--local-folder <folderpath>] [-P|--port <port|8888>]
    # Usage: tsuru local-deploy update -a|--app <appname> [-p|--process <processname>] [-l|--local-folder <folderpath>] [-P|--port <port|8888>] [-c|--copy-environment]
    # Usage: tsuru local-deploy delete -a|--app <appname>
    tsuru local-deploy start -a TSURU_APP

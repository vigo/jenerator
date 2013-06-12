# Jenerator

I've prepared for a simple html skeleton with using open-source libraries.

## Libraries

* [Twitter Bootstrap 2.3.2][01]
* [Font Awesome 3.1.1][02]
* [Less 1.3.3][03]
* [Retina.js 0.0.2][04]
* [jQuery 1.9.1 ][05]

[01]: https://github.com/twitter/bootstrap
[02]: https://github.com/FortAwesome/Font-Awesome
[03]: https://github.com/cloudhead/less.js
[04]: https://github.com/imulus/retinajs
[05]: https://github.com/jquery/jquery

## Download and Install

Just [download][download] and extract.

[download]: https://github.com/vigo/jenerator/archive/v0.1.zip

## Local Server

I assumed that you are running OSX or Linux and already have a python!
Use this little bash function, add it to your environment. `.bashrc` or
how ever you use...

```bash
function server() {
    if [[ $1 == "-h" || $1 == "--help" ]]; then
        echo "usage:"
        echo -e "\tserver PORT"
        echo -e "\tserver # default port is 8000"
        echo
        echo "-h, --help: help"
        echo
        return 0
    fi
    local port="${1:-8000}"
    # open "http://localhost:${port}/"
    python -m SimpleHTTPServer "$port"
    python -c $'import SimpleHTTPServer;\n
                map = SimpleHTTPServer.SimpleHTTPRequestHandler.extensions_map;\n
                map[""] = "text/plain";\n
                for key, value in map.items():\n\t
                map[key] = value + ";charset=UTF-8";\n
                SimpleHTTPServer.test();' "$port"
}
_server()
{
    local cur prev opts
    COMPREPLY=()
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"
    opts="8000 -h --help"

    if [[ ${cur} == * ]] ; then
        COMPREPLY=( $(compgen -W "${opts}" -- ${cur}) )
        return 0
    fi
}
complete -F _server server
```

To execute server type `server`

## Change Log

* **2013-06-12** : started

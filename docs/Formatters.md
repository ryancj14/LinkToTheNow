https://pypi.org/project/mjson/

Project description
This module is extended “python -mjson.tool”.

Install
$ pip install mjson
How to use
Same the original

$ echo '{"a":1,"b":2}' | mjson
{
    "a": 1,
    "b": 2
}
Change indents

$ echo '{"a":1,"b":2}' | mjson -i 2
{
  "a": 1,
  "b": 2
}
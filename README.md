xnpm
====

An experiment to use [sparkfun](https://data.sparkfun.com) to record how and when I use the `npm` command.

### Code

```
# the xnpm function
function xnpm () {
  # run npm command as usual
  npm $@

  # encode url to escape spaces
  command="npm%20"`echo $@ | sed 's/ /%20/g'`

  # send request to sparkfun
  curl -s -o /dev/null "https://data.sparkfun.com/input/PUBLIC_KEY?private_key=PRIVATE_KEY&command=$command" 2>&1
}

# alias npm to xnpm
alias npm='xnpm'

```

Replace the `PRIVATE_KEY` and `PUBLIC_KEY` with your own.

The `command` params is the field you need to set when create a new Data Stream. Here I only need to care which command I was running. `sparkfun` will add the timestamp by default.

### Result

Here's what I got from sparkfun.

command | timestamp
------------ | -------------
npm uninstall lodash  | 2014-07-11T14:35:52.934Z
npm install lodash  | 2014-07-11T14:35:28.257Z
npm uninstall carcass | 2014-07-11T10:55:34.478Z
npm install jingfm-cli  | 2014-07-11T10:55:15.835Z
npm install carcass | 2014-07-11T10:39:20.927Z
npm install underscore  | 2014-07-11T10:38:56.556Z
npm install underscore  | 2014-07-11T10:37:22.145Z
npm -v  | 2014-07-11T10:34:33.590Z
npm install lodash  | 2014-07-11T10:34:22.230Z
npm install lodash  | 2014-07-11T10:29:33.790Z
npm install cnpm  | 2014-07-11T10:27:10.949Z
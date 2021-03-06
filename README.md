# better-regex

## Installation
`npm install --save better-regex`

## Include in your app
```html
<script src="dist/better-regex.umd.js"></script>
const {regex} = window.betterRegex
```

```html
<script type="module">
  import { regex } from './node_modules/better-regex/dist/better-regex.js' 
</script>
```

```ecmascript 6
// main.js
import { regex } from 'better-regex'
```

```ecmascript 6
// node
const { regex } = require('better-regex')
```

## Purpose
Template Tag that allows:
   - composing regular expressions
   - breaking expressions across multiple lines
   - commenting expression parts

### Basic Usage:
```
> const dateRegex = regex`
    (?<year>[0-9]{4})     ## year
    -
    (?<month>[0-9]{2})    ## month
    -
    (?<day>[0-9]{2})      ## day
  `
> const { year, month, day } = dateRegex.exec('2019-01-12').groups
```

### Advanced Usage (composition and config):
```
> const title = regex`(?<title>mr|mrs|dr|ms)`
> const suffix = regex`(?<suffix>jr|sr)`
> const fullNameRegex = regex({flags: 'i'})`
   ^
   ${title}?                ## get title if exists (Mr, Ms, etc)
   \.?
   [ ]?
   (?<firstName>[a-zA-Z]+)  ## pull firstName out into named group
   [ ]
   (?<lastName>[a-zA-Z]+)   ## pull lastName out into named group
   [ ]?
   ${suffix}?               ## you can compose regex's using normal template literal syntax
   \.?
   $
 `
> const { title, firstName, lastName, suffix } = fullNameRegex.exec(`Mr. Cody Landry Sr`).groups
```


### TODO:
- Add tests
- Improve docs

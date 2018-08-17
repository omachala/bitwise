## Permissions example

```javascript
    const permissions = ['read', 'write', 'execute', 'delete'];

    window.calculate = function (permArray) {
        return permArray.reduce((acc, value) => {
            let index = permissions.indexOf(value);
            return index === -1 ? acc : (acc | (1 << index));
        }, 0);
    };

    // calculate(['read','write']);
    // --> 3

    window.verify = function (permNumber, permArray) {
        return permNumber === (permNumber | window.calculate(permArray));
    };

    // verify(3, ['write'])
    // --> true

    // verify(3, ['delete'])
    // --> false
```

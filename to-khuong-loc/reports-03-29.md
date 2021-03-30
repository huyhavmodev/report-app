# Basic-algorithm-scripting: một số cách xử lí với string

## 1. toCapitalize()

_JS không có hàm xử lý tự động convert chữ đầu trong string in hoa_

```javascript
function toCapitalize(str) {
  return str
    .split(" ")
    .map((word) => {
      const lowerWord = word.toLowerCase();
      return lowerWord.replace(
        lowerWord.charAt(0),
        lowerWord.charAt(0).toUpperCase()
      );
    })
    .join(" ");
}

// I'm A Little Tea Pot
toCapitalize("I'm a little tea pot");

// Short And Stout
toCapitalize("sHoRt AnD sToUt");

// Here Is My Handle Here Is My Spout
toCapitalize("HERE IS MY HANDLE HERE IS MY SPOUT");
```

## 2. Truncate a StringPassed

_Ẩn bớt string khi quá dài_

```javascript
    const truncateString(str, num) {
      if(str.length > num) {
        return str.slice(0, num) + "..."
      }
      return str;
    }

    // A-tisket...
    truncateString("A-tisket a-tasket A green and yellow basket", 8);

    // A-tisket a-tasket A green and yellow basket
    Peter Piper...
    truncateString("A-tisket a-tasket A green and yellow basket", "A-tisket a-tasket A green and yellow basket".length)

    // Peter Piper...
    truncateString("Peter Piper picked a peck of pickled peppers", 11)
```

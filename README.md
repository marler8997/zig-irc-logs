This repository hosts the IRC logs for the `#zig` channel on irc.libera.chat.  Logs are stord in `year/month-day.txt` (years are subfolders to keep directories from getting too many entries).

At the end of each day, a new commit is added to the repo with all the new messages for that day, along with a new branch that contains a file just for that day.  This makes it easy for clients to download the entire history, or individual days.

# Format

```
TIMESTAMP\nUSER\nMESSAGE\n\n
```

For example:
```
1619831132
mr_joey
hello, this is a message

1619831140
jarjar
this is another message

```

The reason for this format is that is contains only 1 special character `\n`.  Since neither the `TIMESTAMP`, `USER` nor `MESSAGE` can contain the `\n` character, there is no need for an escape mechanism.  Given a string of one of these files, it can be parsed like this:

```javascript
const entries = file_content.split("\n")
for (var i = 0; i + 2 < entries.length; i++) {
    const timestamp = entries[0];
    const from = entries[1];
    const msg = entries[2];
}
```

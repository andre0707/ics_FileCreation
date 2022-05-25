# .ics file creation
A small readme file how to create a `.ics` calendar file which includes a map location object on iOS devices.
The important part is the `X-APPLE-STRUCTURED-LOCATION` identifier.


## JavaScript example

Here is the JavaScript code which can be used inside a click event to create and show the `.ics` file.
Safari will prompt a message popover to ask the user to display a calendat event first though.

```javascript
const lines = [
    "BEGIN:VCALENDAR",
    "VERSION:2.0",
    "CALSCALE:GREGORIAN",
    "PRODID:-//myApp",
    
    "BEGIN:VEVENT",
    "DTSTAMP:20220516T190341Z",
    "DTSTART;TZID=Europe/Berlin:20220528T120000",
    "DTEND;TZID=Europe/Berlin:20220528T180000",
    "LAST-MODIFIED:20220516T190333Z",
    "CREATED:20220516T190333Z",
    "SUMMARY:The title of the calendar event",
    "STATUS:CONFIRMED",
    "LOCATION:N 50° 40.000' E 008° 40.000'",
    "X-APPLE-STRUCTURED-LOCATION;VALUE=URI;X-APPLE-REFERENCEFRAME=0;",
    "X-TITLE=N 50° 40.000' E 008° 40.000':geo:50.66667,8.66667",
    "UID:A871F3EA-C5EA-49CA-BB70-C5A2E8AF3159",
    "URL;VALUE=URI:https://myurl.com",
    "SEQUENCE:0",
    "X-APPLE-TRAVEL-ADVISORY-BEHAVIOR:AUTOMATIC",
    "DESCRIPTION:Here is some description \\n\\nNext line after empty line",
    
    "BEGIN:VALARM",
    "X-WR-ALARMUID:3219EC9E-9EA2-4693-A252-314A2C84916B",
    "UID:3219EC9E-9EA2-4693-A252-314A2C84916B",
    "TRIGGER:-PT2H",
    "DESCRIPTION:Reminder",
    "ACTION:DISPLAY",
    "END:VALARM",
    
    "END:VEVENT",
    
    "END:VCALENDAR"
];

const durl = 'data:text/calendar;charset=utf-8,'+encodeURIComponent(lines.join('\r\n'));
window.open(durl, '_blank');
```

To use new lines in for example the description/note area, you need to use `\\n` instead of just `\n`.


Here is an examle screenshot from the iOS simulator:

<img src="https://github.com/andre0707/ics_FileCreation/blob/main/calendar-entry.png?raw=true" width=400>

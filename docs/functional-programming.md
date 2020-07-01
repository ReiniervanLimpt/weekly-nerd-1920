## Modular programming

During the course of my minor in web development on the HvA i have studied the uses of modular programming, modular programming is a programming technique that seperates different parts of functionality into small independend sets of code that can be addressed only when needed in a calculation or data manipulation.

### Why would i try modular programming

* Modules have their own namespace, meaning you can use variable names which feel intuitive to the data they are containing without polluting the global namespace.
* Modules are reusable, if written correctly and with a single purpose and predictable output modules can be copy pasted into any project you you need their calculations and manipulations in.
* Code is split up into multiple files providing your directories with structure.
* Sectioning off code in smaller scopes makes it easier to collaborate and avoid merge conflicts.

### My experience with modular programming

In my most recent experience of the final assignment of the Web development minor i worked with 4 other programmers to create a prototype of a application which consumes alot of user data. The data we consumed consisted of datasets containing "compliments" and "goals" these objects contained expiry dates and creation dates which values were dates written as `[DD-MM-YYYY TT:TT]`. I wrote this module which calculated how many days you had left to complete a goal.

```javascript
function checkDate(data) {
  const today = new Date();
  const date = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
  const expiryDate = new Date(data);
  const currentDate = new Date(date);
  const timeBetweenDates = expiryDate - currentDate;
  const timeToExpiry = Math.floor(timeBetweenDates / (3600000 * 24));
  const daysAfterExpiry = timeToExpiry.toString().substring(1);

  if (currentDate > expiryDate) {
    const result = `${daysAfterExpiry} dagen geleden verlopen`;
    return result;
  } else if (expiryDate > currentDate) {
    const result = `${timeToExpiry} dagen om je doel te behalen`;
    return result;
  }
}

module.exports = checkDate;
```
Module is called with `goalsToCheck.forEach(element => element.daysToExpiry = dateChecker(element.expiry_date));`
This is a very specific module which can easiliy be altered for reuse.

With some small tweeks to the code this module could be made to return the amount of days between the date given to the module and the current dat so that my colleague Michel could use my module to calculate how many days ago a comment was placed.

### rewriting the module for reuse
At this moment the module returns a very specific string that is not helpfull in any other page than the goals page of our application, lets rewrite that.

`daysAfterExpiry` is not very usefull and serves no purpose in calculating how many days are between the current date and the parameter given to the module, this rule only removed the - before a date prior to the current date (one week ago is -7)

```javascript
if (currentDate > expiryDate) {
  const result = `${daysAfterExpiry} dagen geleden verlopen`;
  return result;
} else if (expiryDate > currentDate) {
  const result = `${timeToExpiry} dagen om je doel te behalen`;
  return result;
}
```
> this entire section of code was written specifically for the goals page and can be removed.

Leaving us with:

```javascript
function checkDate(data) {
  const today = new Date();
  const date = today.getFullYear() + '-' + (today.getMonth() + 1) + '-' + today.getDate();
  const expiryDate = new Date(data);
  const currentDate = new Date(date);
  const timeBetweenDates = expiryDate - currentDate;
  const timeToExpiry = Math.floor(timeBetweenDates / (3600000 * 24));
  return timeToExpiry
}

module.exports = checkDate;
```

Now my colleagues can call this module with `dateChecker(anyDateValue)` which will return `-7` if the date is a week ago and `7` if it is in the next week.

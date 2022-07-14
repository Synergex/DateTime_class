# DateTime_class<br />
**Created Date:** 1/7/2009<br />
**Last Updated:** 10/12/2010<br />
**Description:** Datetime is a class that Represents an instant in time, typically expressed as a date and time of day. This should not be confused with the Synergy Language 'datetime' function. (Update for Synergy 9.5 compatibility)<br />
**Platforms:** Windows; Unix; OpenVMS<br />
**Products:** Synergy DBL<br />
**Minimum Version:** 9.1.5b<br />
**Author:** Tod Phillips
<hr>

**Additional Information:**
DESCRIPTION: SynDateTime is a class that Represents an instant in time, typically expressed as a date and time of day.

ADDITIONAL NOTES: In order to use this class, it must first be prototyped with the DBLPROTO
utility. Ensure that your SYNIMPDIR and SYNEXPDIR environment variables
have been set, then run the protyper by typing:

dblproto SynDateTime

from a command prompt in the directory where the SynDateTime.dbl file has
been saved. (Alternately, import the file into a Workbench project, right-
click the project in the Projects tab and select "Generate Synergy
Protypes..."). The included file can then be compiled and added to any
library or ELB. To use the provided class methods, simply type

import SynPSG.System

at the top of your source code. (See Example, below).

CLASS: SynDateTime (Public)

ENUMERATION(S): <br/>
Public Enumeration DayOfWeek <br/>
Sunday ,0 <br/>
Monday <br/>
Tuesday <br/>
Wednesday <br/>
Thursday <br/>
Friday <br/>
Saturday <br/>
Private Enumerations TimeValueType <br/>
Millisecond ,0 <br/>
Second <br/>
Minute <br/>
Hour <br/>
Day <br/>
Month <br/>
Year <br/>

CONSTRUCTOR: <br/>
SynDateTime (Public) <br/>
Overloaded. Initializes a new instance of the SynDateTime structure. <br/>

PROPERTIES: <br/>
Date <br/>
Gets the date component of this instance. <br/>
Day <br/>
Gets the day of the month represented by this instance. <br/>
DayOfWeek <br/>
Gets the day of the week represented by this instance. <br/>
DayOfYear <br/>
Gets the day of the year represented by this instance. <br/>
Hour <br/>
Gets the hour component of the date represented by this instance. <br/>
Millisecond <br/>
Gets the milliseconds component of the date represented by this instance. <br/>
Minute <br/>
Gets the minute component of the date represented by this instance. <br/>
Month <br/>
Gets the month component of the date represented by this instance. <br/>
Now <br/>
Gets a SynDateTime object that is set to the current date and time on this computer, expressed as the local time. <br/>
Second <br/>
Gets the seconds component of the date represented by this instance. <br/>
SynDate <br/>
Gets the date as a Synergy decimal value expressed as YYYYMMDD (d8). <br/>
TimeOfDay <br/>
Gets the time of day for this instance. <br/>
Today <br/>
Gets the current date. <br/>
Year <br/>
Gets the year component of the date represented by this instance. <br/>


METHOD(S): <br/>
AddDays (Public) <br/>
Adds the specified number of days to the value of this instance. <br/>
AddHours (Public) <br/>
Adds the specified number of hours to the value of this instance. <br/>
AddMilliseconds (Public) <br/>
Adds the specified number of milliseconds to the value of this instance. <br/>
AddMinutes (Public) <br/>
Adds the specified number of minutes to the value of this instance. <br/>
AddMonths (Public) <br/>
Adds the specified number of months to the value of this instance. <br/>
AddSeconds (Public) <br/>
Adds the specified number of seconds to the value of this instance. <br/>
AddYears (Public) <br/>
Adds the specified number of years to the value of this instance. <br/>
DaysInMonth (Public Static) <br/>
Returns the number of days in the specified month and year. <br/>
IsLeapYear (Public Static) <br/>
Returns an indication whether the specified year is a leap year. <br/>
ToLongDateString (Public) <br/>
Converts the value of this instance to its equivalent long date string representation. <br/>
ToLongTimeString (Public) <br/>
Converts the value of this instance to its equivalent long time string representation. <br/>
ToShortDateString (Public) <br/>
Converts the value of this instance to its equivalent short date string representation. <br/>
ToShortTimeString (Public) <br/>
Converts the value of this instance to its equivalent short time string representation. <br/>
ToString (Public) <br/>
Converts the value of this instance to its equivalent string representation. <br/>
DateInvalid (Private) <br/>
Determines whether the current instance represents a valid date. <br/>


EXAMPLE(S):

The following program demonstrates the use of the SynDateTime class.

;; Program to demonstrate the SynDateTime class.

import SynPSG.system <br/>
main <br/>
record <br/>
myDT ,@SynDateTime <br/>
endrecord <br/>
proc <br/>
open(1,o,"TT:") <br/>
myDT = SynDateTime.Now <br/>
writes(1, "Current date: "+myDT.ToString("d")) <br/>
writes(1, "In 35 minutes it will be: " + myDT.AddMinutes(35).ToString()) <br/>
writes(1, "Note that the current date is still: " + myDT.ToString()) <br/>
writes(1, "Today is day "+%string(myDT.DayOfYear)+" of the year "+%string(myDT.Year)) <br/>
myDT = myDT.AddMonths(4) <br/>
writes(1, "Four months from now, there will be "+%string(SynDateTime.DaysInMonth(myDT.Year,myDT.Month))+" days in the month.") <br/>
writes(1, "In Synergy YYYYMMDD format, that date will be represented as "+%string(myDT.SynDate)+".") <br/>
myDT = new SynDateTime(19991231) <br/>
writes(1, "The last day of the last century was " + myDT.ToLongDateString()) <br/>
endmain

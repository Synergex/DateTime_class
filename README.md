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

ENUMERATION(S):
Public Enumeration DayOfWeek
Sunday ,0
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Private Enumerations TimeValueType
Millisecond ,0
Second
Minute
Hour
Day
Month
Year

CONSTRUCTOR:
SynDateTime (Public)
Overloaded. Initializes a new instance of the SynDateTime structure.

PROPERTIES:
Date
Gets the date component of this instance.
Day
Gets the day of the month represented by this instance.
DayOfWeek
Gets the day of the week represented by this instance.
DayOfYear
Gets the day of the year represented by this instance.
Hour
Gets the hour component of the date represented by this instance.
Millisecond
Gets the milliseconds component of the date represented by this instance.
Minute
Gets the minute component of the date represented by this instance.
Month
Gets the month component of the date represented by this instance.
Now
Gets a SynDateTime object that is set to the current date and time on this computer, expressed as the local time.
Second
Gets the seconds component of the date represented by this instance.
SynDate
Gets the date as a Synergy decimal value expressed as YYYYMMDD (d8).
TimeOfDay
Gets the time of day for this instance.
Today
Gets the current date.
Year
Gets the year component of the date represented by this instance.


METHOD(S):
AddDays (Public)
Adds the specified number of days to the value of this instance.
AddHours (Public)
Adds the specified number of hours to the value of this instance.
AddMilliseconds (Public)
Adds the specified number of milliseconds to the value of this instance.
AddMinutes (Public)
Adds the specified number of minutes to the value of this instance.
AddMonths (Public)
Adds the specified number of months to the value of this instance.
AddSeconds (Public)
Adds the specified number of seconds to the value of this instance.
AddYears (Public)
Adds the specified number of years to the value of this instance.
DaysInMonth (Public Static)
Returns the number of days in the specified month and year.
IsLeapYear (Public Static)
Returns an indication whether the specified year is a leap year.
ToLongDateString (Public)
Converts the value of this instance to its equivalent long date string representation.
ToLongTimeString (Public)
Converts the value of this instance to its equivalent long time string representation.
ToShortDateString (Public)
Converts the value of this instance to its equivalent short date string representation.
ToShortTimeString (Public)
Converts the value of this instance to its equivalent short time string representation.
ToString (Public)
Converts the value of this instance to its equivalent string representation.
DateInvalid (Private)
Determines whether the current instance represents a valid date.


EXAMPLE(S):

The following program demonstrates the use of the SynDateTime class.

;; Program to demonstrate the SynDateTime class.

import SynPSG.system
main
record
myDT ,@SynDateTime
endrecord
proc
open(1,o,"TT:")
myDT = SynDateTime.Now
writes(1, "Current date: "+myDT.ToString("d"))
writes(1, "In 35 minutes it will be: " + myDT.AddMinutes(35).ToString())
writes(1, "Note that the current date is still: " + myDT.ToString())
writes(1, "Today is day "+%string(myDT.DayOfYear)+" of the year "+%string(myDT.Year))
myDT = myDT.AddMonths(4)
writes(1, "Four months from now, there will be "+%string(SynDateTime.DaysInMonth(myDT.Year,myDT.Month))+" days in the month.")
writes(1, "In Synergy YYYYMMDD format, that date will be represented as "+%string(myDT.SynDate)+".")
myDT = new SynDateTime(19991231)
writes(1, "The last day of the last century was " + myDT.ToLongDateString())
endmain

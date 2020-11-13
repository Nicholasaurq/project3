# project3
Nicholas Urquhart

The beginning of the program will convert the log file to a list for easy parsing throughout the program.
re.split() distiguishes spaces in an entry and whitespace, so now there are no premature cutoffs or extra entries
3 functions will handle 4 of the problems. Iresponsible behavior and glitches are basically similar procresses, so i decided to combine both into one function


WEEK 3 UPDATE
Many changes since attempting to implement the approach:
the system of parsing through the log info is a number system. Since the email starts at 0, and all each entry in the log info remains consistent through all entries,
I've decided to parse through the files by starting at 3. This is where the email always is, and if we need the info from date, we can just subtract i(being the index of where the email is) -3. -2 for login/logout, and -1 for server. This is why you don't see any of the "for i in range" loops start at 0, but rather 3.

The approach of methods has stayed the same. However, one change was neccesarry. I created a new method called sortLog so that organizing the reports by date and time is much easier. This method takes in the list of entries, and sorts it into a dictionary where the key is the date, and its values are all of the activity that occurs on that day.
For example:
05-01 : list of all activity on 05-01
05-02: list of all activity on 05-02
The creation of this method was actaully the longest and hardest part of the process. The method works by create an empty ditionary, creating a integer n, which counts up to 30, this is for choosing which day to parse for. Then for every entry in the list, if it finds a date that has the same day as the one it is parsing for, it will append all the information for that log info following the date to the dictionary. Once it is done with that, we have a dictionary sorted by date, but not by time. That is where I used a bubble sort alogrithm that I know how to do from a prior programming class. Simply put, for each entry in every list, if the first date is later than the first date, then the user info gets switched. This does not end until it can go through the list and not make one switch.

Since Irr Behave and Sys Glitches are essentially inverses of each other, we can, as we are counting up login/logouts, have logins increase a dictinary storing email and difference of logins/logouts with logouts decreases the number by 1, determine if there is either irresponsible behavior or a
system glitch. A user has committed an irresponsible behavior if that number is greater than 0, and we know if the system glitched if it is less than one. This means proper login/logouts equal 0.


Domains is quite simple, it is the only method that does not use the sorted log. This goes through the entry list, if it finds a new domain, it adds it to the key dicitonary. If it finds a new user using that domain, it will add one to the value.

Suspicious activities method actauly uses much of the code from the Irr Behave and sys Gltich method. Its only logic changed is that the dictionary stores logins only, and increases by one each new login. Also, for easy determination, if the suspicious activity is by an after hours login (12AM to 5AM), then ii will increase logins by 400. Since 400 logins is unachieable only by a 12AM to 5AM login, we will know what dtermines it, an arrow is used to indicate an after hours login.

Here were three problems I ran into:

1. Managing the number system and the numerous for loops. A lot of thinking and reminding of where I am at in parsing or calculation was needed. I sometimes ran into issues where i used the wrong index.


2.sortLog took up nearly the majority of time spent on the project. I originally thought this would be a quick process to make orgainzation easier. However, I found myself spending alot of time debugging and interpretting how to handle the problem. I ran into one problem that took me hours to figure out, only to find out the problem was just a mistype of a variable.


3.Towards the end of the project, while going through my checks, I realized that, while the first few reports were correct, later on down the report, irresonible behaviors and  system glitches was only showing dates on the last day. This also, while took a while, was a simple fix. I realized that the dictionary storing the user as the key and its value being the difference of logins/logouts, it was essentially being wiped everytime a new day started. So I had to move all of my logic for irr behave and sys glitches into one of for loops. This meant that in order to print total number of cases, I needed to write everything to file, while also counting total number of cases, then have all the text equal a variable, wipe the file, then write the header, number of cases, and then rewrite all of the log info. This had to happen for both reports.

This felt like a very large project, and took me 8+ hours. I personally can't help feel like there was a more effecient way of going about all of this. However after already creating much of the code and flowcharts, I didn't want to ditch everything and start over.

# techesthete-assessment

##Booking Controller

1 - index

early return used when the first condition matches. elsif block removed.
the function should return a default null or other response in both above conditions fail. or we can throw exception.

2 - show.
 
 no refactor.
 
3 - store.
 
 no refactor.
 
4 - update.
 
 refactored $cuser as $current_user. better readability.
 moved the array_except method call outside of function call and stored in a var and pass that var.
 
5 - immediateJobEmail

unused var $adminSenderEmail. could be a mistake or error. its misleading so removed.

6- getHistory

early returned null when no user_id present in request.. and move all code that was in the if block outside.
reason for this is that the code within if block has the tendency to grow bigger. its better we keep it outside to avoid nested code.

7- acceptJob

no refactor.

8- acceptJobWithId

no refactor.

9- cancelJob

no refactor

10- endJob

no refactor.

11- customerNotCall

rename the function name to customerNotCalled

12- getPotentialJobs

unused $data variable is misleading. remove it.

13- distanceFeed

i - early return used for the case of flagged comment and when the admincomment value is empty.
ii - all else cases removed by initilization the vars in begining and also using empty function instead of isset will do both the job of checking isset and the empty value.
iii - the string 'no' is going to be treated as truthy value.. it should be replaced with boolean false.

14- reopen
 
no refactor

15- resendNotifications

no refactor

16- resendNotifications

no refactor

17- resendSMSNotifications

$job_data is unused and the function call to jobToData() method is just return that unused array. hence removed.

##BookingRepository

this is a repository class. I will only put query and data related functions in a repository class and not logic.
but i notice that this class contain both database queries and logic. the logical code can be separated out into a different
class maybe a service class. Also this class is so huge and its like a god class. doing lots of stuff.. i will refactor this class
into many different classes using the first SOLID principle i.e SRP (single responsibility principle).

i have given my suggestion for few functions.

1- __construct

using new operator to created instances is not a good practise as it may break the code because its possible
that the class dependencies will change. hence its better to use the laravel Dependency injection to init these class 
objects.

2- getUsersJobs

removed else blocks and used early return. improved code indentation.

3- getUsersJobsHistory

replaced elseif with if.
this function does not contain a default return value.. this can cause error and bugs.. should return a value
when no if check is met.

4- store

this function is huge. doing a lot of stuff. it should be refactored into a separate class that have the
single responsibility of storing booking. within that class use private methods 
to describe logic .. for example i created a private method isNotImmediate() and put all the checks in there.
this increase readability.

5- storeJobEmail

looks fine. i remove an else block.

6- jobToData

refactored the code and create two private methods that removes the complexity around if/else checks.

7- jobEnd

refactored one else statement. this function is using the new keyword to instantiate objects which can 
cause error if constructor argument changes for the class. maybe its better to use the app() helper function
to resolve instance from the laravel container. one other benefit this provide is if you use phpunit to unit test your 
code as you bind your mocking to the container.

8- getPotentialJobIdsWithUserId

if else statements are missing the curly brackets {} .. its a good practice to always use curly brackets
with if statement and for loop etc.

9- sendNotificationTranslator

refactored the code to remove deep indentation of code and made use of private functions to translate logical checks
into readable functions.





 







 
 
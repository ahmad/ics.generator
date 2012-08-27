
## ICS File Generator
This class generates an ICS file that users can download and add to their Calender. It is compatible with any software that supports
standard ICS files which includes Outlook, Google Calander, iCal and many more.

<b>Version 0.2 Released: 04/16/2012</b>

## Usage

The library was designed to be simple and get to you up and running in the shortest amount of time.

### Step 1: Getting the library

I would recommend you download the library directly from my git repository (https://github.com/ahmadamin/ics-generator) because it will always 
be up-to-date with the latest release. All you need is the **invite.php** file which includes the class **Invite** that does all the magic.

### Step 2: Usage

As mentioned above this class was designed to be as simple as possible to use. All that is required is for you to be a little familiar with Object-Oriented
PHP or just understand code at least. If you are not familiar with OO PHP that is not a problem because you can just copy and paste this example below into you project
and modify the details to suite your needs.

I would highly recommend you **do not alter or modify the invite.php file or class**. You should do all your programming and customization in a separate file.
<pre>
// alter path based on where in your file structure the invite.php file is located
require 'invite.php';

$invite = new Invite($unique_id); // You should (not required) provide a UNIQUE ID

// As you may notice this library supports chaining which may be a little weird for many PHP programmer
$invite 
	    ->setSubject("Test Demo Invite")
	    ->setDescription("The is a test invite for you to see how this thing actually works") 
	    ->setStart(new DateTime('2013-03-16 12:00AM EST'))
	    ->setEnd(new DateTime('2013-03-16 11:59PM EST'))
	    ->setLocation("Queens, New York")
	    ->setOrganizer("john@doe.com", "John Doe")
	    ->addAttendee("ahmad@ahmadamin.com", "Ahmad Amin");

$invite -> download();
</pre>
If you do now want to use the chaining method as listed about you can use it as such:

    require 'invite.php';

    $invite = new Invite($unique_id);

    $invite ->setSubject("Test Demo Invite");
    $invite ->setDescription("The is a test invite for you to see how this thing actually works");
    $invite ->setStart(new DateTime('2013-03-16 12:00AM EST'));
    $invite ->setEnd(new DateTime('2013-03-16 11:59PM EST'));
    $invite ->setLocation("Queens, New York");
    $invite ->setOrganizer("john@doe.com", "John Doe");
    $invite ->addAttendee("ahmad@ahmadamin.com", "Ahmad Amin");

    $invite -> download();

The generated output file is **invite.ics**. You can open that file with Outlook or iCal.

### Step 3: Check if downloaded (optional)
If you would like to check and see if the invite has been downloaded or not you can use **Invite::isDownloaded()** method as listed below.

    if(Invite::isDownloaded()){
	    // do something ...
    }

As you may notice the **isDownloaded()** method is a static method so you **do not need to create a new Invite() object to call it**. At anytime you can
use it to check and see if the invite has been downloaded.
### Step 4: Advance Usage
Please look at example/example2.php for a more advance usage method which allows you to generate and save the file to be downloaded at a later time.

### Step 5: Lead More
*I would highly recommend you take a look at the invite.php file for other methods and alias of these methods.*
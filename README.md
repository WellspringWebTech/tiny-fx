tiny-fx
=======

PHP Framework - Flyweight, Robust, Scalable

This framework is very small and minimalistic, therefore it is extremely fast and scalable. With only 123 procedural lines of code as the core, it is very easy to get ones head around this paradigm and start developing in just few minutes. And the paradigm is Modular and Minimalistic. In essence, this framework aims to be the smallest of its kind that serves the whole purpose. It is good for solutions where a large number of requests can be expected.

Modular web apps can be built on this. This framework itself is NOT object oriented, but highly modular. Application developer has the liberty to make each module procedural, modular or object oriented.

This version (2.0) is distinctive from previous TinyF(x) on that this version treats modules as packages, all-inclusive packages that can be ported to another project easily.

==Module==
A module is a segment in a web app. Module has methods. An HTTP request loads a module, calls a method in it, and responds with HTML, JSON or XML.

Let's assume you are building a web app for example.com domain. An HTTP request received to http://example.com/dashboard/messages/ calls for the module 'dashboard'. The module 'dashboard' is loaded first. Then the method 'messages' is called. This method should be expecting one parameter, an array of request parameters in it, along with any proceeding url segment. Method is expected to return an array, or exit. If a method returns an array, a corresponding view is loaded. Elements of the array becomes variabled for the view file.

==View==
A view is a php file inside a module containing mostly HTML markup. As in previous example, when the method for 'messages' returns an array, the view 'messages' inside the 'dashboard' module is rendered.

==Template==
Header and Footer, or the common parts for a lot of simillar web pages can be put in to one php file. A template is an outer frame for a web page. You can have any number of templates in a project. Usually a template is associated to each module. Of cource many or all modules can use same template, and some methods in a module can go with a different template other than the template set for the module. Template is defined at the top of module, and can be overwritten from anywhere in the module.
i.e: $template_file = "admin.php";

==Interfaces==
Interfaces are some libraries to make development easier. To send an Email, Connect to a database, zip some files, resize images there are interfaces. You can simply include these files inside methods and use their functions. These are documented inside each one. You can contribute by writing more of these.

==Database Abstraction==
Database abstraction is carried out by an object oriented interface [module]. Set database credentials in config.php
First you have to do this:
$db = connect_database();

After that you can do these things:
$db->query('SELECT * FROM messages WHERE userid = 3');
$db->insert('table_name', array('column' => 'value', 'id' => 4), 'userid = 3');
$db->update('table_name', array('column' => 'value', 'id' => 4));

In insert and update, if the primary key is 'id', the framework takes care of it all. You don't have to worry about where clause at all.

You don't have to include a file for this. The interface is included after you call this function. Calling this function again will only return a pointer to the same object (singleton). But, if you want to connect to another database on the same server with same credentials, pass the database name as the first parameter to the same function. This will return a new object for database connection to the second database. So, basically you can connect to several databases at the same time.

==Sending Email==
There is an interface for that.! Include 'interfaces/email.php' then call send_email($to, $data, $template, $subject, $attachments) . $data should be an associative array, the sort of you should return from a method. The $template is the view which is rendered against $data.

==Making image thumbnails, or resize==
There is an interface for that too.! Include 'interfaces/image_magic.php'. Resize or make thumbnails without worrying about cropping and preserving the ratio. Just tell the required size, this will crop as necessory and resize it nicely.


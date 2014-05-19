tiny-fx
=======

PHP Framework - Flyweight, Robust, Scalable

This framework is very small and minimalistic, therefore it is extremely fast and scalale. With only 123 procedural lines of code as the core, it is very easy to get ones head around this paradigm and start developing in just few minutes. And the paradigm is Modular and Minimalistic. In essence, this framework aims to be the smallest of its kind that serves the whole purpose. It is good for solutions where a large number of requests can be expected.

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
Database abstraction is carried out by an object oriented interface [module]. First you have to do this:
$db = connent
After that you can do these things:

==Sending Email==
There is an interface for that.! Include 'interfaces/email.php' then call send_email($to, $data, $template, $subject, $attachments) . $data should be an associative array, the sort of you should return from a method. The $template is the view which is rendered against $data.

==Making image thumbnails, or resize==
There is an interface for that too.! Include 'interfaces/'


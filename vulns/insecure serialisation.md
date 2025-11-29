# PHP
php provides several magic methods that play crucial roles in the serialisation process:
- `__sleep()`: This method is called on an object before serialisation. It can clean up resources, such as database connections, and is expected to return an array of property names that should be serialised.
- `__wakeup()`: This method is invoked upon deserialisation. It can re-establish any connections that the object might need to operate correctly.
- `__serialize()`: As of PHP 7.4, this method enables you to customise the serialisation data by returning an array representing the object's serialised form.
- `__unserialize()`: This counterpart to `__serialize()` allows for customising the restoration of an object from its serialised data.
p.s.
you might be able to access backup files with ~ at the end
there is an automation tool called PHP Gadget Chain (PHPGGC) if you ever need it
# Python
python uses pickle and allows you to fully serialise objects without having to worry about whats serialised, as it actually serialises the full object
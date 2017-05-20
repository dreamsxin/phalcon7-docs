Abstract class **Phalcon\\Acl\\Adapter**
========================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Acl\\AdapterInterface <Phalcon_Acl_AdapterInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/acl/adapter.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Acl\\Adapter initializer


Methods
-------

public  **setDefaultAction** (*int* $defaultAccess)

Sets the default access level (Phalcon\\Acl::ALLOW or Phalcon\\Acl::DENY)



public *int*  **getDefaultAction** ()

Returns the default ACL access level



public *string*  **getActiveRole** ()

Returns the role which the list is checking if it's allowed to certain resource/access



public *string*  **getActiveResource** ()

Returns the resource which the list is checking if some role can access it



public *string*  **getActiveAccess** ()

Returns the access which the list is checking if some role can access it



public  **setDI** (:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector) inherited from Phalcon\\Di\\Injectable

Sets the dependency injector



public :doc:`Phalcon\\DiInterface <Phalcon_DiInterface>`  **getDI** ([*unknown* $error], [*unknown* $notUseDefault]) inherited from Phalcon\\Di\\Injectable

Returns the internal dependency injector



public  **setEventsManager** (:doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>` $eventsManager) inherited from Phalcon\\Di\\Injectable

Sets the event manager



public :doc:`Phalcon\\Events\\ManagerInterface <Phalcon_Events_ManagerInterface>`  **getEventsManager** () inherited from Phalcon\\Di\\Injectable

Returns the internal event manager



public *boolean*  **fireEvent** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified



public *boolean*  **fireEventCancel** (*string* $eventName, [*unknown* $data], [*unknown* $cancelable]) inherited from Phalcon\\Di\\Injectable

Fires an event, implicitly calls behaviors and listeners in the events manager are notified This method stops if one of the callbacks/listeners returns boolean false



public *mixed*  **fireEventData** (*string* $eventName, [*mixed* $data]) inherited from Phalcon\\Di\\Injectable

Fires an event, return data



public *boolean*  **hasService** (*string* $name) inherited from Phalcon\\Di\\Injectable

Check whether the DI contains a service by a name



public :doc:`Phalcon\\Di\\ServiceInterface <Phalcon_Di_ServiceInterface>`  **setService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Sets a service from the DI



public *object|null*  **getService** (*unknown* $name) inherited from Phalcon\\Di\\Injectable

Obtains a service from the DI



public *mixed*  **getResolveService** (*string* $name, [*unknown* $args], [*unknown* $noerror], [*unknown* $noshared]) inherited from Phalcon\\Di\\Injectable

Resolves the service based on its configuration



public  **attachEvent** (*string* $eventType, *Closure* $callback) inherited from Phalcon\\Di\\Injectable

Attach a listener to the events



public  **__get** (*unknown* $property) inherited from Phalcon\\Di\\Injectable

Magic method __get



public  **__sleep** () inherited from Phalcon\\Di\\Injectable

...


public  **__debugInfo** () inherited from Phalcon\\Di\\Injectable

...


abstract public *boolean*  **addRole** (:doc:`Phalcon\\Acl\\RoleInterface <Phalcon_Acl_RoleInterface>` $role, [*string* $accessInherits]) inherited from Phalcon\\Acl\\AdapterInterface

Adds a role to the ACL list. Second parameter lets to inherit access data from other existing role



abstract public  **addInherit** (*string* $roleName, *string* $roleToInherit) inherited from Phalcon\\Acl\\AdapterInterface

Do a role inherit from another existing role



abstract public *boolean*  **isRole** (*string* $roleName) inherited from Phalcon\\Acl\\AdapterInterface

Check whether role exist in the roles list



abstract public *boolean*  **isResource** (*string* $resourceName) inherited from Phalcon\\Acl\\AdapterInterface

Check whether resource exist in the resources list



abstract public *boolean*  **addResource** (:doc:`Phalcon\\Acl\\ResourceInterface <Phalcon_Acl_ResourceInterface>` $resource, [*array* $accessList]) inherited from Phalcon\\Acl\\AdapterInterface

Adds a resource to the ACL list Access names can be a particular action, by example search, update, delete, etc or a list of them



abstract public  **addResourceAccess** (*string* $resourceName, *mixed* $accessList) inherited from Phalcon\\Acl\\AdapterInterface

Adds access to resources



abstract public  **dropResourceAccess** (*string* $resourceName, *mixed* $accessList) inherited from Phalcon\\Acl\\AdapterInterface

Removes an access from a resource



abstract public  **allow** (*string* $roleName, *string* $resourceName, *mixed* $access, [*unknown* $callback]) inherited from Phalcon\\Acl\\AdapterInterface

Allow access to a role on a resource



abstract public *boolean*  **deny** (*string* $roleName, *string* $resourceName, *mixed* $access, [*unknown* $callback]) inherited from Phalcon\\Acl\\AdapterInterface

Deny access to a role on a resource



abstract public *boolean*  **isAllowed** (*string* $role, *string* $resource, *string* $access, [*unknown* $data]) inherited from Phalcon\\Acl\\AdapterInterface

Check whether a role is allowed to access an action from a resource



abstract public :doc:`Phalcon\\Acl\\RoleInterface <Phalcon_Acl_RoleInterface>` [] **getRoles** () inherited from Phalcon\\Acl\\AdapterInterface

Return an array with every role registered in the list



abstract public :doc:`Phalcon\\Acl\\ResourceInterface <Phalcon_Acl_ResourceInterface>` [] **getResources** () inherited from Phalcon\\Acl\\AdapterInterface

Return an array with every resource registered in the list




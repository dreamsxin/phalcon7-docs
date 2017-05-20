Class **Phalcon\\Mvc\\Model\\Transaction\\Manager**
===================================================

*extends* abstract class :doc:`Phalcon\\Di\\Injectable <Phalcon_Di_Injectable>`

*implements* :doc:`Phalcon\\Events\\EventsAwareInterface <Phalcon_Events_EventsAwareInterface>`, :doc:`Phalcon\\Di\\InjectionAwareInterface <Phalcon_Di_InjectionAwareInterface>`, :doc:`Phalcon\\Mvc\\Model\\Transaction\\ManagerInterface <Phalcon_Mvc_Model_Transaction_ManagerInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/mvc/model/transaction/manager.c" class="btn btn-default btn-sm">Source on GitHub</a>`

A transaction acts on a single database connection. If you have multiple class-specific databases, the transaction will not protect interaction among them.  This class manages the objects that compose a transaction. A trasaction produces a unique connection that is passed to every object part of the transaction.  

.. code-block:: php

    <?php

    try {
    
      use Phalcon\Mvc\Model\Transaction\Manager as TransactionManager;
    
      $transactionManager = new TransactionManager();
    
      $transaction = $transactionManager->get();
    
      $robot = new Robots();
      $robot->setTransaction($transaction);
      $robot->name = 'WALL·E';
      $robot->created_at = date('Y-m-d');
      if($robot->save()==false){
        $transaction->rollback("Can't save robot");
      }
    
      $robotPart = new RobotParts();
      $robotPart->setTransaction($transaction);
      $robotPart->type = 'head';
      if($robotPart->save()==false){
        $transaction->rollback("Can't save robot part");
      }
    
      $transaction->commit();
    
    }
    catch(Phalcon\Mvc\Model\Transaction\Failed $e){
      echo 'Failed, reason: ', $e->getMessage();
    }



Methods
-------

public  **__construct** ([:doc:`Phalcon\\DiInterface <Phalcon_DiInterface>` $dependencyInjector])

Phalcon\\Mvc\\Model\\Transaction\\Manager constructor



public :doc:`Phalcon\\Mvc\\Model\\Transaction\\Manager <Phalcon_Mvc_Model_Transaction_Manager>`  **setDbService** (*string* $service)

Sets the database service used to run the isolated transactions



public *string*  **getDbService** ()

Returns the database service used to isolate the transaction



public :doc:`Phalcon\\Mvc\\Model\\Transaction\\Manager <Phalcon_Mvc_Model_Transaction_Manager>`  **setRollbackPendent** (*boolean* $rollbackPendent)

Set if the transaction manager must register a shutdown function to clean up pendent transactions



public *boolean*  **getRollbackPendent** ()

Check if the transaction manager is registering a shutdown function to clean up pendent transactions



public *boolean*  **has** ()

Checks whether the manager has an active transaction



public :doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>`  **get** ([*boolean* $autoBegin])

Returns a new Phalcon\\Mvc\\Model\\Transaction or an already created once This method registers a shutdown function to rollback active connections



public :doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>`  **getOrCreateTransaction** ([*boolean* $autoBegin])

Create/Returns a new transaction or an existing one



public  **rollbackPendent** ()

Rollbacks active transactions within the manager



public  **commit** ()

Commmits active transactions within the manager



public  **rollback** ([*boolean* $collect])

Rollbacks active transactions within the manager Collect will remove transaction from the manager



public  **notifyRollback** (:doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>` $transaction)

Notifies the manager about a rollbacked transaction



public  **notifyCommit** (:doc:`Phalcon\\Mvc\\Model\\TransactionInterface <Phalcon_Mvc_Model_TransactionInterface>` $transaction)

Notifies the manager about a commited transaction



protected  **_collectTransaction** ()

Removes transactions from the TransactionManager



public  **collectTransactions** ()

Remove all the transactions from the manager



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



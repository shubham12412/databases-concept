# databases-concept

1) transactions

2) Structured Query Language (SQL)

3) TRANSACTIONS, ACID-ITY, AND TWO-PHASE COMMIT

In addition to the features mentioned already, RDBMSs and SQL also support transactions.  A key feature of transactions is that they execute  virtually at first, allowing the programmer to undo (using rollback) any changes that may have gone awry during execution; if all has gone well, the transaction can be reliably committed.  As Jim Gray puts it, ***a transaction is “a transformation of state” that has the ACID properties*** (see “The Transaction Concept: Virtues and Limitations”).

http://jimgray.azurewebsites.net/papers/thetransactionconcept.pdf

ACID is an acronym for Atomic, Consistent, Isolated, Durable, which are the gauges we can use to assess that a transaction has executed properly and that it was successful:


Atomic

Atomic means “all or nothing”; that is, when a statement is executed, every update within the transaction must succeed in order to be called successful. There is no partial failure where one update was successful and another related update failed. The common example here is with monetary transfers at an ATM: the transfer requires subtracting money from one account and adding it to another account. This operation cannot be subdivided; they must both succeed.

Consistent

Consistent means that data moves from one correct state to another correct state, with no possibility that readers could view different values that don’t make sense together. For example, if a transaction attempts to delete a customer and her order history, it cannot leave order rows that reference the deleted customer’s primary key; this is an inconsistent state that would cause errors if someone tried to read those order records.

Isolated

Isolated means that transactions executing concurrently will not become entangled with each other; they each execute in their own space. That is, if two different transactions attempt to modify the same data at the same time, then one of them will have to wait for the other to complete.

Durable

Once a transaction has succeeded, the changes will not be lost. This doesn’t imply another transaction won’t later modify the same data; it just means that writers can be confident that the changes are available for the next transaction to work with as necessary.

4)


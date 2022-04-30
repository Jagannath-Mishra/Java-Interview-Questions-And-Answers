# Q.Spring @Transactional - isolation, propagation

```

Good question, although not a trivial one to answer.

## Propagation
Defines how transactions relate to each other. Common options:

REQUIRED: Code will always run in a transaction. Creates a new transaction or reuses one if available.
REQUIRES_NEW: Code will always run in a new transaction. Suspends the current transaction if one exists.
The default value for @Transactional is REQUIRED, and this is often what you want.

## Isolation
Defines the data contract between transactions.

ISOLATION_READ_UNCOMMITTED: Allows dirty reads.
ISOLATION_READ_COMMITTED: Does not allow dirty reads.
ISOLATION_REPEATABLE_READ: If a row is read twice in the same transaction, the result will always be the same.
 ISOLATION_SERIALIZABLE: Performs all transactions in a sequence.
The different levels have different performance characteristics in a multi-threaded application. I think if you understand the dirty reads concept you will be able to select a good option.
```

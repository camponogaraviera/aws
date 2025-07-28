<div align='center'>
  <h1> Databases </h1>
</div>

# Table of Contents

- [RDS for PostgreSQL](#rds-for-postgresql)
- [DynamoDB](#dynamodb)
  - [DynamoDB Stream](#dynamodb-stream)
- [Neptune](#neptune)
  - [Pricing](#pricing)
- [Aurora](#aurora)

---

# [RDS for PostgreSQL](https://aws.amazon.com/rds/postgresql/)

"Amazon RDS for PostgreSQL gives you access to the capabilities of the familiar PostgreSQL database engine. This means that the code, applications, and tools you already use today with your existing databases can be used with Amazon RDS." —AWS.

---

# [DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)

DynamoDB is a NoSQL database for storing unstructured and semi-structured data. Resort to the dedicated section [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/database/technologies/dynamodb.md).

## [DynamoDB Stream](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html)

DynamoDB Stream can be used to propagate changes in DynamoDB Tables and enable multi-region active-active data storage.

---

# [Neptune](https://aws.amazon.com/pt/neptune/)

AWS Neptune is a graph database. It is vendor lock-in and, therefore, integrates seamlessly with other AWS services. Available query languages are Apache TinkerPop Gremlin and SPARQL. Neptune is ACID-compliant.

## Pricing 

AWS Neptune has an on-demand instance pricing. You pay for:

1) Storage: billed per GB-month.
2) I/Os: billed per million requests.
3) Compute instance.

---

# [Aurora](https://aws.amazon.com/rds/aurora/)

Aurora is a relational database that is compatible with MySQL and PostgreSQL, but some features differ.

## Examples of Many-To-Many Relationships

- A products table and a suppliers table - Products may have 0 to many suppliers, and suppliers can supply 0 to many products.
- A classes table and a students table - Students can take potentially many classes and classes can have many students enrolled.


## Joining Table

Joining tables help define many-to-many relationships between data in a database. As an example when defining the relationship above between products and suppliers, we would define a joining table called products_suppliers that contains the primary keys from the tables to be joined.

Then, when we want to see if a supplier supplies a specific product, we can look in the joining table to see if the ids share a row.

## Unique Constraint Across 2 Fields

When enforcing specific schema constraints we may need to enforce the UNIQUE constraint across two different fields.

```
CREATE TABLE product_suppliers (
  product_id INTEGER,
  supplier_id INTEGER,
  UNIQUE(product_id, supplier_id)
);
```

This lets multiple rows share the same product_id or supplier_id, but it prevents any two rows from having both the same product_id and supplier_id.


## Composite key

When we're talking more generally about data normalization, the term "primary key" means the collection of columns that uniquely identify a row. That can be a single column, but it can actually be any number of columns that form a composite key. A primary key is the minimum number of columns needed to uniquely identify a row in a table.

If you think back to the many-to-many joining table product_suppliers, that table's "primary key" was actually a combination of the 2 ids, product_id and supplier_id:

```
CREATE TABLE product_suppliers (
    product_id INTEGER,
    supplier_id INTEGER,
    UNIQUE(product_id, supplier_id)
);
```

# normalization

## 1st Normal Form (1NF)

To be compliant with first normal form, a database table simply needs to follow 2 rules:

- It must have a unique primary key.
- A cell can't have a nested table as its value (depending on the database you're using, this may not even be possible)

## 2nd Normal Form (2NF)

A table in second normal form follows all the rules of 1st normal form, and one additional rule which only applies to composite primary keys:

- All columns that are not part of the primary key are dependent on the entire primary key, and not just one of the columns in the primary key.


## Rules of Thumb for Database Design

1. Every table should always have a unique identifier (primary key)
2. 90% of the time, that unique identifier will be a single column named id
3. Avoid duplicate data
4. Avoid storing data that is completely dependent on other data. Instead, compute it on the fly when you need it.
5. Keep your schema as simple as you can. Optimize for a normalized database first. Only denormalize for speed's sake when you start to run into performance problems.













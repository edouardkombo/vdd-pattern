## Welcome to Vocabulary Driven Database Pattern

VDD pattern (Vocabulary Driven Database Pattern) is Single Responsibility pattern and DRY principle brought to database architecture. It consists of a set of structured tables with their relationships, helping to:
1. Build readable schemas
2. Scale database schemas from an early stage
3. Adopt better sharding strategies
4. Better design micro-services architectures

Founded by Edouard Kombo, the VDD pattern aims to be supported by a collaborative community. A shared vocabulary makes it easier for developers and architects to decide on a schema and get the maximum benefit for their efforts.


### Introducing the "Me" paradigm

Everything starts from a user perspective. The "Me" paradigm's philosophy is to make this perspective very personal, by replacing "user" or any other term defining a user,  by "me".


### The laws of Vocabulary Driven Database Pattern

Me:
- is a table (entity) containing only an identifier (id)
- has xToMany relations with other entities following Single Responsibility pattern

When to create dedicated tables:
- when columns have xToMany relationships with the parent table
- if a column has oneToOne relation with the parent table, define your own rule based on filling percentage (columns with data / columns without data)


### Getting started

We want to create a user system in which users are able to:
- Register with first name, last name, username, gender, email, date of birth, phone number, address, zip code, region and country
- Login with email (or any other field) and password
- Send a message to another user
- Chat
- Have a status (active, inactive, disable or many others)
- Be banned for a specific reason
- Delete their own profile or other relations
- Block another user or entity for a specific reason
- Report a suspicious activity

```
# We create the table "me" containing only one column: "id"

# We use the wonderful sharedapi.org for common entities like countries, cities, towns, regions, skills, genders (DO NOT REPEAT YOURSELF, DO NOT REINVENT THE WHEEL)

Then we create xToMany relations to these Single Responsibility tables
- secret                # Me can protect anything with a password, just like his relations (DRY)
- gender                # Me can change gender whenever he wants
- skill                 # Me can change skill whenever he wants
- civility              # Me posseses a civility, firstname, lastname and date of birth
- email                 # Me can have one or many email addresses, as some of his relations
    - email_status      # Email can be confirmed or not
- ownership             # Me has an ownership status with specific types ("owner, tenant, visitor...")
- phone                 # Me can have one or multiple phone numbers, as some of his relations
    - phone_country     # A phone number is attached to one country
- address               # Me can have multiple addresses, as some of his relations. Contains "street and number"
    - address_country   # An address is attached to a country
    - address_city      # An address is attached to a city
    - address_region    # An address is attached to a region    
    - address_zipcode   # An address is attached to a zipcode
    - address_ownership # An address is attached to Me through an ownershipe
    - address_deleted   # In case of multiple addresses, we can find the active one
- follow                # Me can follow other "Me"s or relations
    - follow_status     # An entity can be unfollowed and refollowed again
- relationship          # Me can be related to other "Me"s
    - relationship_type # "friend, mother, uncle, sister, etc"
- channel               # Me can subscribe to channels listned by many other "Me"s
    - channel_deleted   # A channel can be deleted"
    - channel_jailed    # On decision after a reporte
    - channel_report    # Self explaining
- message               # Me can just write messages
    - message_channel   # Message can be linked to a channel
    - message_me        # Message can be linked to another "Me"
    - message_deleted   # The owner can delete a message"
    - message_jailed    # On decision after a report
    - message_status    # In case of multiple addresses, we can find the active one
    - message_report    # Self explaining
- status                # Me just like his relations may have statuses
    - status_type       # Statuses can be linked to various entities with types (active, inactive)  
- deleted               # Any entity linked to this table is considered removed
- report                # Self explaining
    - report_type       # Self explaining
- jailed                # Me can be put in jail for a specific period
    - jailed_type       # Jailed type is really custom (permanent, temporary, etc...)
    - jailed_reason     # Self explaining
- reason                # Self explaining
    - reason_type       # Self explaining
- blocked               # Me can be put in jail for a specific period
    - blocked_type      # Me and Other relations only (like: "message")
    - blocked_reason    # Self explaining      
```


### Support or Contact

Feel free to contribute to this project, for any support please contact me at edouard.kombo@gmail.com and I will be more than likely to help you.

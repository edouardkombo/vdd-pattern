## Welcome to Vocabulary Driven Database Pattern

Founded by Edouard Kombo, VDD pattern or "Me paradigm" is a collaborative community with the mission to create, maintain and promote schemas for structured databases following DRY principle, and starting exclusively from a user perspective. 

VDD vocabularies cover entities, relationships between entities and actions, and can easily be extended through a well-documented extension model.

A shared vocabulary makes it easier for developers and architects to decide on a schema and get the maximum benefit for their efforts.


### Understand the pattern

VDD's philosophy or "me paradigm" starts from a "user" perspective who:
- is always a representation of "me"
    - "me" is only an identifier (id)
    - "me" can not exist without an identifier (id), but
    - "me" can exist without relations
    - "me" has oneToMany relations to multiple attributes called entities
- does not repeat himself (DRY)
    

### Get started

Let's design a simple user system with those attributes: password, gender, skills, firstname, lastname, email. date of birth, phone number, address, country.

```
# We create the table "me" containing only one column: "id"

# We use the wonderful sharedapi.org for common entities like countries, cities, towns, regions, skills, genders (DO NOT REPEAT YOURSELF, DO NOT REINVENT THE WHEEL)

We then create oneToMany relations to these tables
- secret                # Me can protect anything with a password, just like his relations (DRY)
- gender                # Me can change gender whenever he wants
- skill                 # Me can change skill whenever he wants
- civility              # Me posseses a civility, firstname, lastname and date of birth
- email                 # Me can have multiple email addresses, as some of his relations
- ownership             # Me has an ownership status with some relations ("owner, tenant, visitor etc")
- phone                 # Me can have multiple phone numbers, as some of his relations
    - phone_country     # A phone number is attached to one country
- address               # Me can have multiple addresses, as some of his relations. Contains "street and number"
    - address_country   # An address is attached to a country
    - address_city      # An address is attached to a city
    - address_region    # An address is attached to a region    
    - address_zipcode   # An address is attached to a zipcode
    - address_ownership # An address is attached to Me through an ownership
- follow                # Me can follow other "Me"s or relations    
- relationship          # Me can be related to other "Me"s
    - relationship_type # "friend, mother, uncle, sister, etc"

**user** has oneToMany relation with **secret**
**user** has oneToMany relation with **secret**
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/edouardkombo/vdd-pattern/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

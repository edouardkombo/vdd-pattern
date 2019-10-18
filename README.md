## Welcome to Vocabulary Driven Database Pages

Founded by Edouard Kombo, VDD pattern is a collaborative community with the mission to create, maintain and promote schemas for structured databases following DRY principle. VDD vocabularies cover entities, relationships between entities and actions, and can easily be extended through a well-documented extension model.

A shared vocabulary makes it easier for developers and architects to decide on a schema and get the maximum benefit for their efforts.


### Understand the pattern

VDD's philosophy starts from a "user" who:
- is always a representation of "me"
    - "me" is only an identifier (id)
    - "me" can not exist without an identifier (id)
    - "me" only owns oneToMany relations to multiple attributes called entities
    - "me" can exist without relations
- does not repeat himself (DRY)
    

### Get started

Let's design a simple user system with those attributes: password, gender, skills, firstname, lastname, email. date of birth, phone number, address, country.

```
We create the table "me" containing only one column: "id"

We then create oneToMany relations to these tables
- secret                # to store the password because other entities can be password protected too, not only "me" (DRY)
- country               # Me can be linked to multiple countries. Contains "code, name, phone prefix"
- gender                # Me can change gender whenever he wants
    - gender_type       # Gender is expected to be a human, but can also be an animal (oneToMany relation with gender)
- skill                 # Me can change skill whenever he wants
    - skill_type        # Skills must be grouped by type  (oneToMany relation with skill)
- civility              # Contains firstname, lastname and date of birth related to Me
- email                 # Me can have multiple email addresses, as some of his relations
- phone                 # Me can have multiple phone numbers, as some of his relations
    - phone_country     # A phone number is attached to one country
- address               # Me can have multiple addresses, as some of his relations. Contains "street and number"
    - address_country   # An address is attached to a country
    - address_town      # An address is linked to a town
    - address_ownership # An address is linked to Me through an ownership ("owner, tenant, visitor etc")
- town                  # Me can be linked to multiple towns, as some of his relations
- zipcode               # Me can have multiple phone numbers, but also some of his relations
    - address_zipcode   # A phone number can be attached to one country
- relation              # Me can have multiple phone numbers, but also some of his relations
    - relation_type     # A phone number can be attached to one country

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


``` npm install postgresql-orm --save ```

```
var ORM = require('postgresql-orm')

ORM.setup('postgres://<username>:<password>@<hostname>/<dbname>')

var User = new ORM('User') // will match table with name 'users'

// save or update, depending on the presence of an 'id' attribute
User.save({name: 'John'}, function(err, savedEntity) {
	// do something
	savedEntity.id
})

User.create({firstName: 'John'}, function(err, createdEntity) {
	// do smthg
})

User.update({id: 123, lastName: 'Doe'}, function(err, updatedEntity) {
	// do smthg
})

User.load({id: 123}, function(err, loadedEntity) {
	// do smthg
})
```

notes
-----

- for each table, an auto-generated type column named ``id`` is required
- attributes starting with an underscore are reserved
- camel case attributes are transformed into snake case.
  - For example attributeName will map to column attribute_name
	- the behaviour is undefined if there are 2 attributes attributeName and
		attribute_name for one entity type as the resulting column names are the
		same.

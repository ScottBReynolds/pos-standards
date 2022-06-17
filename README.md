# Unofficial Standards for PlatformOS

These standards are based off the PlatformOS Core Concepts. [Read this first](https://documentation.platformos.com/developer-guide/pos-marketplace-template/core-concepts#general-rules)

## Purpose:
The intention is to create a more uniform way to structure and "code" a PlatformOS project. When a PlatformOS project adheres to community standards readability, maintainability, and reusability are improved.

### Benefits of standards:

- Speeds up development
- Lowers development costs
- Avoids duplicated efforts ("reinventing the wheel")
- Aligns the community (reduce fragmentation/silos)
- Increases community support
- Encourages building and sharing compatible components
- Makes it easier to hire freelance pOS developers
- Speeds up onboarding/training

## How to use this guide:
This guide is divided between examples and specific recommendations. You will find examples in the [modules folder](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules). Each module can be used as a reference to see the standards in action, or used as a starting point for your own module.

## Standards
The standards are broken up in to three categories (structure, naming, and coding).

### Structure: 
The example module, [Structure](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/structure), demostrates the recommended structure.

#### template-values.json
To avoid module name collisions modules should include a variable named "module_path". [Example](https://github.com/ScottBReynolds/pos-standards/blob/structure/modules/structure/private/template-values.json)

#### Commands
Commands should be in the commands directory: [views/partials/lib/commands](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/structure/private/views/partials/lib/commands)

#### Queries
Queries should be in the queries directory: [views/partials/lib/queries](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/structure/private/views/partials/lib/queries)


### Naming:

#### ids
When working with queries and mutations, there may be several ids. Properly naming ids will reduce confusion.
##### item_id
Prefix the "main" record id with 'item' (i.e. 'item_id')
##### Secondary ids
Prefix "secondary" ids with object or property name. Examples: user_id, property_id, etc.
#### is_
Functions that return a boolean should be prefixed with 'is_'. (e.g. is_logged_in, is_admin, is_user)

### Coding:

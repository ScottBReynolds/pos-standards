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

### 1. Structure: 
An example module, [Mate](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/mate), demostrates the recommended structure.

#### 1.1 template-values.json
To avoid module name collisions modules should include a variable named "module_path". [template-values.json](https://github.com/ScottBReynolds/pos-standards/blob/structure/modules/mate/template-values.json)

#### 1.2 Commands
Commands should be in the commands directory: [views/partials/lib/commands](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/mate/private/views/partials/lib/commands)

#### 1.3 Queries
Queries should be in the queries directory: [views/partials/lib/queries](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/mate/private/views/partials/lib/queries)


### 2. Naming:
#### 2.1 Module Path
Replace the module path with <%= &module_path =%> 
[See Example](https://github.com/ScottBReynolds/pos-standards/tree/structure/modules/mate/private/graphql/automations/create.graphql)  
Learn about [Module Templates.](https://documentation.platformos.com/developer-guide/modules/templates#content)
#### 2.2 ids
When working with queries and mutations, there may be several ids. Properly naming ids will reduce confusion.
##### 2.2.1 item_id
Prefix the main record id with item (i.e. item_id). [See Example](https://github.com/ScottBReynolds/pos-standards/search?q=item_id)
##### 2.2.2 Secondary ids
Prefix "secondary" ids with object or property name. Examples: user_id, property_id, etc.
#### 2.3 Functions
##### 2.3.1 Name
Function names should match the path of the command or query. object_action. (e.g. function users_find = 'modules/chat/lib/queries/users/find')
##### 2.3.2 is_
When representing a boolean the name should be prefixed with is_. (e.g. is_logged_in, is_admin, is_background_job) [See Example](https://github.com/ScottBReynolds/pos-standards/search?q=is_background_job)
#### 2.4 GraphQL
##### 2.4.1 Aliases
 - item(s) => record(s)
 - item(s) => user(s)
 - item_id => id
 - page_num => page
 - limit => per_page

### 3. Coding:
#### 3.1 Page (function + render)
Instead of hard coding each page, get data with a function tag (views/partials/lib/commands or queries) and output with a render tag (views/partials/themes). This helps keep code clean and simple to read.
##### (views/pages/index)
```
{% liquid
    function data = 'lib/commands/data', id: id
    render 'themes/simple/data', data: data
%}
```

#### 3.2 Themes
Themes (views/partials/themes) is a concept that uses the liquid render tag to output HTML, or JSON etc without polluting it with unessasary code used to collect or create data. Data is supplied directly to the theme but not retrieved, maniplulated or created inside the theme.

###### (views/pages/index)
```
{% liquid
    function data = 'lib/commands/data', id: id
    render 'themes/simple/data', data: data
%}
```

###### (views/partials/themes/simple/index)
```
<h1>{{ data.title }}</h1>
```
This help keep code used to render the page clean and makes creating alternate themes easier as they only use data supplied to them.


<h1 align="center"><img src="assets/icon.png" width="100" height="100"></br>DEVONthink 3 Portal</h1>



**Use A** ` dvn [ ] [ . ] [ {query} ] `

- `dvn ` No input displays all available databases
- `dvn .` Displays global actionable options
- `dvn {query}` Initiate global search
	- Supports all DEVONthink 3 prefixes and wildcards


**Use B** ` ddvn [ {query} ] `  
- `ddvn {query}` triggers a file filter brute-force search (fast)


## Features (Selection)

- Global and Database Search
- Tag Search with auto suggest
- Document Actions (move, replicate, duplicate, create annotation file, etc.)
	- Extra: Get BibTex or formatted citation from DOI, ISBN or existing BibTeX [^1]
- Multiple Document Actions (move, replicate, open all, **reciprocal linking**, etc.)
- Navigate the Folder Structure
- Import New Documents to Location
- Customizable Annotation Templates
- Copy Page Link for open PDF documents
- Colored Labels (customize as needed)
	- Colored Flags on labeled records


## Actionable Options

**Global Options** Trigger: ` dvn . `

- Find Groups
- Show Favorites
- Show Reading List
- Filter Smart Groups
- Load Workspace
- Save Workspace
- Find records similar to a given string 
	- Impacted by the configuration variable `Score Threshold`

**Database Options** Trigger: ` dvn |dbs|2| . `

- Find Groups in Database
- Access to Default Groups
	- Inbox
	- Annotations
	- Trash
	- Tags (autocompletes to tag search)

---

## Details

### Search

#### Default Search

The search behaves the same as in DEVONthink, but by default only returns documents, i.e. groups, smart groups and tag groups are ignored. The workflow respects DEVONthink prefixes, operators and wildcards, giving you full control over the query. Some examples: 
- `name:~keyword` 
- `name:<keyw kind:!ordinarytag` 
- `keyword {any: tags:affekt*;ratio*}`

This also allows you set up custom hotkeys by providing the desired query as argument to the workflow input.  
- [Reference for Search Prefixes](file:///Applications/DEVONthink%203.app/Contents/Resources/DEVONthink.help/Contents/Resources/pgs/appendix-searchprefixes.html)
- [Reference for Search Operators](file:///Applications/DEVONthink%203.app/Contents/Resources/DEVONthink.help/Contents/Resources/pgs/appendix-operators.html)

The default comparison method is `Case Insensitive`, which can be changed in the workflow configuration.  

#### Tag Search

Queries can be refined with tags at any point. Type the octothorp symbol and start typing the name of the desired tag. The workflow will auto suggest tags you have defined in DEVONthink. 

Tags come in three flavors: `#tag #tag? #!tag`
- `#tag` defines a strict requirement (show only documents that have this tag)
- `#tag?` defines an optional requirement (show documents that either have this tag, or another optional tag)
- `#!tag` defines a tag that is to be excluded (do not show documents that have this tag)

**Modifiers**

Tag suggestions can be autocompleted to match the above mentioned flavors.
- `default` the document must have this tag (resolves to `#tag`)
- `cmd` the document must not have this tag (resolves to `#!tag`)
- `opt` the document may have this tag (resolves to `#tag?`)

### Modifiers



### Custom Metadata 

The workflow responds to the following DEVONthink custom metadata identifiers:

- `mddoi`: DOI
- `mdisbn`: ISBN
- `mdlink`: Link
- `mdlinkedrecords`: Linked Records (configurable) [^2]


### Annotation Templates

You can create custom templates that will be used when creating an *annotation file* for some record, i.e. a markdown document that is associated with it. You can customize your templates in `/assets/annotations`. These `placeholder` variables are currently supported:
- `%recordName%`
- `%documentLink%`
- `%year%`
- `%month%`
- `%day%`
- `%hour%`
- `%minute%`


## Plugins

- µBib
- PDF Expert


## Notes

- Supports DEVONthink 3.8.7 or later. Version 3.8.7 brought breaking changes to the scripting bridge.
- TIP: Fine-tuning the threshold becomes more interesting the larger your database grows. High thresholds for small databases can be detrimental to accuracy.

## Endnotes


[^1]: Optional. Requires the `µBib` Workflow to be installed (`WIP`). DEVONthink will try to automatically extract DOIs from documents. However, this does not always succeed. You can help DEVONthink out by adding a custom metadata field with the identifier `DOI`. [µBib on Github](https://www.github.com/zeitlings/alfred-ubib/) (WIP).

[^2]: Attention! Potentially replaces preconfigured data.
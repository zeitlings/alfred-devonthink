<h1 align="center">
    <img src="assets/devonthink_icon.png" width="100" height="100"></br>
    DEVONthink 4 Portal</br>
    <a href="https://github.com/zeitlings/alfred-devonthink/releases"><img src="https://img.shields.io/github/v/release/zeitlings/alfred-devonthink.svg?logo=alfred&label=download" alt="GitHub Release"></a>
</h1>

<a href='https://ko-fi.com/G2G1IH7RR' target='_blank'><img height='36' align='right' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi1.png?v=3' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

---

Advanced DEVONthink 4 interface for your databases

## Usage

__Search your databases__ via the `dvn` keyword, using any [prefix](https://download.devontechnologies.com/download/devonthink/3.8.2/DEVONthink.help/Contents/Resources/pgs/appendix-searchprefixes.html), wildcard, or [operator](https://download.devontechnologies.com/download/devonthink/3.8.2/DEVONthink.help/Contents/Resources/pgs/appendix-operators.html) also available in DEVONthink. 

Use the [Universal Action](https://www.alfredapp.com/help/features/universal-actions/) to __import documents__ to a specific location.
To either jump to the global __group search__, or the active __document winows__, use the `dvng` or `dvna` convenience keywords. 
Set up the [Hotkey Trigger](https://www.alfredapp.com/help/workflows/triggers/hotkey/) to act on your __current selection__ in DEVONthink.
Alternatively, use the `ddvn` keyword for a fast brute force query over your documents.

### Usage Details

`dvn [⎵] [ . ] [ query ]`

- `dvn ` Show all databases.
- `dvn .` Show globally available actions.
- `dvn query` Search globally in all databases.
- `dvn ?` Show internal configuration.

<img src="assets/previews/dvn-entry.png" width="564px"/>

## Feature Overview (Selection)

- Global and Database Search
- ~~Tag Search with Auto Suggest~~
- Document actions 
    - move, replicate, duplicate, create annotation file, find similar items, etc.
	- >`Extra` Get the BibTeX reference or CSL formatted citation from a DOI, ISBN or jstore URL.  
	  > CSL formatted citations can also be generated from an existing BibTeX reference.[^1]
- Multiple document actions 
    - move, replicate, open all, **reciprocal linking**, etc. 
    - > __Note__[^2]
- Navigate the folder structure
- Import new documents to location
- Customizable annotation templates
- Colored labels (customize as needed)
	- Colored flags on labeled records
- Copy page link for open pdf documents


## Actionable Options

**Global Options** Trigger: ` dvn . `

- Find Groups
- Show Favorites
- Show Reading List
- Today
- Recently Modified
- Recently Added
- Recently Opened
- Due Soon
- Overdue
- Filter Smart Groups
- Load Workspace
- Save Workspace
- Delete Workspace
- Find Records similar to a given String
	- Affected by the `Score Threshold` configuration variable

**Database Options** Trigger: ` dvn |dbs|2| . `

- Find Groups in Database
- Access Default Groups & Filters
    - Inbox
	- Annotations
	- Trash
	- Tags (autocompletes to tag search)
    - Today
    - Recently Modified
    - Recently Added
    - Due Soon
    - Overdue
---

## Search

### Default Search

The search behaves the same as in DEVONthink, but by default only returns documents, i.e. groups, smart groups and tag groups are ignored. The workflow respects DEVONthink prefixes, operators and wildcards, giving you full control over the query. Examples: 
- `name:~keyword` 
- `name:<keyw kind:!ordinarytag` 
- `keyword {any: tags:affekt*;ratio*}`
- `judgement label:2` or, for instance, `judgement label:urgent`

<!-- This also allows you set up custom hotkeys by providing the desired query as argument to the workflow input. -->

> __Note__  
> Within the database root or any folder, typing an asterisk `*` will return the entire contents of that location.

Reference for [__Search Prefixes__](https://download.devontechnologies.com/download/devonthink/3.8.2/DEVONthink.help/Contents/Resources/pgs/appendix-searchprefixes.html).  
Reference for [__Search Operators__](https://download.devontechnologies.com/download/devonthink/3.8.2/DEVONthink.help/Contents/Resources/pgs/appendix-operators.html).

### Tag Search
  
> Currently unavailable in Dt4Portal v2.0.0

Queries can be refined with tags at any point. Type the octothorp symbol and start entering the name of the desired tag. The workflow will auto suggest tags from your DEVONthink databases. 

Tags come in three flavors:
- `#tag` defines a strict requirement (show only documents that have this tag)
- `#tag?` defines an optional requirement (show documents that either have this tag, or another optional tag)
- `#!tag` defines a tag that is to be excluded (do not show documents that have this tag)

**Autocomplete Modifiers**

Tag suggestions can be autocompleted to match the above mentioned flavors.
- `default` the document must have this tag (`#tag`)
- `cmd` __⌘__ the document must not have this tag (`#!tag`)
- `opt` __⌥__ the document may have this tag (`#tag?`)


<details>
<summary>Expand for preview</summary>

<img src="assets/previews/dvn-tagsearch.png" width="564px"/>
</details>


## Entry Point and Search Results

<img src="assets/previews/dvn-entry.png" width="564px"/>

- `default` Enter Database Search
- `cmd` __⌘__ List all Tags in Database
- `opt` __⌥__ Open Database in DEVONthink

<img src="assets/previews/dvn-dbs1.png" width="564px"/>

- __⌘1__ `⏎` return key steps into the parent group
- __⌘2__ `⏎` return key steps into the targeted group


### Search Results

<img src="assets/previews/dvn-db-search.png" width="564px"/>

Press the `⏎` return key to access the [actions](#record-actions) available for the record.

| Modifier 	| Action 	| Configuration 	|
|---:		|:--		|:---:			|
| `cmd` 	| Display Tags 	|  	|
| `opt` 	| Open in DEVONthink or Default Application 	| ⦿ 	|
| `ctrl` 	| Reveal in DEVONthink 	|  		|
| `shift` or `cmd+Y` 	| Quick Look Preview 	|  	|
| `cmd+L` 	| Large Type showing the File Name, Location and Tags 	|  	|
| `fn` 		| View the score of the record (responds to the configured *threshold*)	| ⦿ 	|

> __Note__  
> Press the `⏎` return key while the workflow is retrieving the search results to launch DEVONthink with the given query.

## Record Actions

| <img src="assets/previews/dvn-record-action1.png" width="564px"/> |
|:--:|
| Record Actions - A |

### ` ⌘2 ` The Main Record

Press the `⏎` return key to open the record in DEVONthink or the default application for the file type (Configuration).

| Modifier 	| Action 	| Configuration 	|
|---:	|:---	|:---:	|
| `cmd`  	| Open in default application or in DEVONthink 	| ⦿ 	|
| `cmd+c` 	| Copy item link or page link if the record is open in a DEVONthink document window 	| ⦿ 	|
| `cmd+shift` 	| Copy Markdown Link 	|  	|
| `opt+shift` 	| Copy page link (unless set as default) 	| ⦿ 	|
| `opt` 	| Reveal in DEVONthink 	|  	|

### ` ⌘5 ` Move Record

Press the `⏎` return key to select a new location for the record. If the record has replicants, you will have to decide which instance to move on a subsequent view (Configuration).

### ` ⌘8 ` Instances (Configuration)

Press the `⏎` return key to explore the instances, that is, replicants and duplicates of the record.

<details>
<summary>Expand to preview</summary>

<img src="assets/previews/dvn-instances.png" width="564px"/>

</details></br>

### ` ⌘9 ` Create an Annotation File for the Record

If an annotion file already exists for the record, that file is displayed instead.

> __Note__ See [`Annotation Templates`](#annotation-templates)

---

| <img src="assets/previews/dvn-record-action2.png" width="564px"/> |
|:--:|
| Record Actions - B |

### ` ⌘2 ⌘3 ` DOI and ISBN

| Modifier 	| Action 	| Configuration 	|
|---:		|:---		|:---:			|
| `cmd` 	| Get the BibTeX reference or CSL formatted citation via the *µBib Workflow* | ⦿ |
| `cmd+c` 	| Copy to clipboard | |

### ` ⌘4 ` BibTeX 

| Modifier 	| Action 	| Configuration 	|
|---:		|:---		|:---:			|
| `cmd` 	| Get CSL formatted citation via the *µBib Workflow* | ⦿ |
| `cmd+c` 	| Copy to clipboard | |

### ` ⌘7 ⌘8 ` Incoming and Outgoing Links

View incoming or outgoing (wiki) links or mentions. 
> __Note__  
> *Linking records* together injects references into the custom metadata of the records, which are registered by DEVONthink as inbound or outbound links. See [`On Reciprocal Linking`](#on-reciprocal-linking)



## Hotkey and Universal Action

You can send your selection to the `dvn Universal Action` from either the file system or from within DEVONthink. To act on the records currently selected in DEVONthink, you can also use the hotkey `cmd+shift+D` by default. 

<img src="assets/previews/dvn-hotkey-dt3-selection.png" width="564px"/>
<img src="assets/previews/dvn-import.png" width="564px"/>

The most recently used import location is remembered for quick access. The number of remembered import locations can be defined in the Wokflow Configuration.


### Buffered Records

You can push records to Alfreds file buffer to perform actions on all of them, such as moving, replicating, or linking them together. 

<img src="assets/previews/dvn-buffer1.png" width="564px"/>

Send all buffered items to the Universal Action interface with ⌥+▶

<img src="assets/previews/dvn-buffer2-universal-action1.png" width="564px"/>

<img src="assets/previews/dvn-buffer3-universal-action2.png" width="564px"/>


## On Reciprocal Linking


> __Warning__  
> Potentially replaces preconfigured data if the custom metadata identifier `mdlinkedrecords` is already in use. Change this value in the configuration to avoid conflicts if necessary.

<!-- 
<details>
<summary>Expand to see more information</summary>

WIP. For now, make sure the custom metadata field `mdlinkedrecords` is not taken or change it in the configuration to avoid conflicts.

</details> 
-->


## Custom Metadata 

The workflow responds to the following DEVONthink custom metadata identifiers:

- `mddoi`: DOI
- `mdisbn`: ISBN
- `mdlink`: Link
- `mdlinkedrecords`: Linked Records (Configuration[^2])


## Annotation Templates

You can create custom templates that will be used when creating an *annotation file* for some record, i.e. a markdown document that is associated with it. You can customize your templates in `/assets/annotations`. These `placeholder` variables are currently supported:
- `%recordName%`
- `%documentLink%`
- `%year%`
- `%month%`
- `%day%`
- `%hour%`
- `%minute%`


## Plugins

- [**µBib**](https://www.github.com/zeitlings/ubib/) | *Citations, BibTeX, and Research*
- **PDF Expert** Copy the DEVONthink page link for the page currently viewed in PDF Expert


## Configuration

<img src="assets/previews/dvn-config.png" width="564px"/>

Some internal configuration options are available via `dvn ?`
- Open Workflow Configuration
- Browse Annotation Templates
- Browse Workflow Cache
- Browse Workflow Data
- Show Documentation
- Clear Cache

### Labels

Currently it is not possible to extract the names you have assigned to your labels directly from DEVONthink. However, you can enter them into the text field where they are picked up by the workflow. 

The colored icons for the labels are located in `./icons/labels` and `./icons/labels_flagged`. If you want different colored icons, you have to replace the existing icons with new ones.


---

# Notes

- Supports DEVONthink 3.8.7 or later. Version 3.8.7 brought breaking changes to the scripting bridge.
- `Tip` Fine-tuning the threshold becomes more interesting the larger your database grows. High thresholds for small databases can be detrimental to accuracy.

<!-- # Endnotes -->


[^1]: Optional. Requires the `µBib` Workflow to be installed. DEVONthink will try to automatically extract DOIs from documents. However, this does not always succeed. You can help DEVONthink out by adding a custom metadata field with the identifier `DOI`. [µBib on Github](https://www.github.com/zeitlings/ubib/).

[^2]: Attention! Potentially replaces preconfigured data if the custom metadata identifier for *Linked Records* (`mdlinkedrecords`) is already in use. Change this value in the configuration to avoid conflicts if necessary. 

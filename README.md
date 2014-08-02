# Open Task Format


The Open Task Format (OTF) is a human-readable format for representing task lists.

OTF has a few simple goals:

* Files should be human readable and writable
* Support common, basic features of all services, but complex features may be omitted to ensure import/export between all services
* Moving between services should be a simple export/import task

## Apps
Check out the [otf-utils](https://github.com/tternes/otf-utils) respository for a work-in-progess set of utilities.


---

# Specification (alpha)

## Lists

Lists or projects are collections of tasks. The list format is simple, since only the name of the list is supported in OTF.

| Field | Description |
| ----- | ----------- |
| Name | The name of the list. Some services include an Inbox, which is treated as a normal list by OTF. Importers may select these lists by name as needed. |

Lists are represented in OTF files by wrapping the list name with equals (`=`) characters. Here's an example:

	= House Repairs =

An OTF file with three empty lists would appear as follows:

	= Groceries =
	= House Repairs =
	= Birthday Gifts =


## Tasks

| Field | Description |
| - | - |
| Name | The main content of an individual work item |
| Due Date | An ISO 8601 date indicating when the task is due |
| Completion | Denotes whether or not the task has been completed |
| Star | Designates important or high priority tasks |

Tasks are represented on a single line in OTF, making their information density very high. Each line leads with a set of brackets (`[` and `]`) with a space or `X` to indicate if the task is complete. A star `★` (Unicode U+2605) will follow the brackets for starred tasks. The task name follows, and is proceeded by an optional due date field, contained in another set of brackets.

	= Groceries =
	[ ] Milk
	[X] Cheese
	[ ] ★ Coffee

### Due Date

*TODO...*

# Example

	= List =
	[ ] Incomplete item
	[X] Completed item
		
	= Another List =
	[ ] Something [2014-01-01]
	[ ] Do thing
	[ ] ★ Starred item
	[ ] Something repeats every seven days [2014-01-01,r7d]
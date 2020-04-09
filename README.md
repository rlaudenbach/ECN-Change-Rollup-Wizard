## ECN Change Rollup Wizard v1
- Extends standard ECN capability
- Allows to define change rollup decisions to top, ignore , to level below top)
- Automates adding of impacted items from where used "to affected Items"
- Applies "Float on Release" strategy for parts listed as "fff interchangeable"

### Pre-requisites
Aras Innovator Release: 12SP5
Product Engineering Release: 12R2

### Implementation Details
This package installs on top of standard core. It extends these elements. 

Package PLM:
- adds "foreign" properties to item type "Affected Item".
- adds flag "where use wizard" to item type "ECN"
- unhides "Gen" property on item type "Part"
- adds custom logic to life cycle map "ECN"
- extends query definition and TGV  "PE_BOMStructure" to show "generations"
- adds a list property to "ECN Affected Item"

Package ECN Change Rollup Wizard:
- adds an action to run Where used impact.
- adds logic used with life cycle transition of ECN.
- adds relationship type "ECN WhereUsed Impact"
- adds "signoff" tab with WF History to "ECN"
- adds "Affected how" list to be used with new property on "ECN Affected Item"

### Improvements
- Improve logic "ECNwuRelshipUpdate". apply rules to automaically add interchangeable part in all places. Improve synch with affected items rows (include delete and update scenarios)
- Add capability to Simple ECO
- Add capability to Exprress ECO - and its impact matrix

### Installation Steps
Import is done in 1 step.

1. Use Package Utilities and log on as "admin". Use "merge" option.
	select path to mf file "imports.mf", select all packages  --> click import button

### Usage
load sample data using nash or AML-studio.  3 AML files to be loaded in indicated sequence.
NOTE: 2nd AML command must be applied with user "root" !

- log on as any PE user
- Go to "Parts". And search for P6 and P7
- Select parts P6 and P7, right click and start action "Add Items to Change.."
- On "Select Change" dialog choose "ECN" and "new" and click "OK"
- On newly created ECN enter a title and check "Where Used Impact Wizard Enabled". Then save an close the ECN.
- Re-open the ECN to see new tab "Where Used Impact"
- Put ECN in "Edit" mode and open this tab. In column "fff interchangeable Item" enter "P2" for each row where "P2" is listed in the path.
- Also, in column "fff interchangeable Item" enter "Top" for row with path "/P3/P10/Top"
- Now save the ECN. Then go to tab "Affected Items" to see item that got added automatically from where used impact settings.
- step through the ECN workflow until it is released

- Open the 3 test assembles "P1", "P10", "P8".
- Review their multi level BOMs to see the new revisions in the right places.

NOTE: 
- Of the top assembles only "P10" has a new revision.
- P2 has not received a new revision, but its children show new revision for part "P5" and "P6"

## Credits


## License
This project is published under the MIT license. See the [LICENSE file](./LICENSE.md) for license rights and limitations.)

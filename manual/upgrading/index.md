---
---
# Upgrading
When evolving simple-acme, we strive for backwards compatibility and in-place upgrades. A typical upgrade can be 
deleting everything from the program directory and extracting the new files from the [download](/download) page. This can even be automated by 
tools like [Scoop](https://github.com/lukesampson/scoop).

There are some cases when you might want to be a little more careful. 

- If you made changes to the [example scripts](/manual/advanced-use/examples) included with the distributed `.zip`-file, you will probably want to preserve those. We do accept PR's for scripts, so if they are the type of changes which others might find useful too, please feel free to submit them.
- If you've developed your own plugins, they might need to be updated for a major release (e.g. moving from 2.3.x to a future 2.4.x), because this generally means that either the .NET runtime has been upgrade or some plugin interfaces have been modified.

## From win-acme
simple-acme is an xcopy upgrade for any 2.x.x version of win-acme.

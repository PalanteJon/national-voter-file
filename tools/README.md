#The Tools we Use
This document explains how to install the tools you need to work on the national voter file project.

## Pentaho Data Integration
Pentaho Data Integration (PDI) is also know as Kettle. It's an opensource Extract/Transform/Load tool that 
allows us to be productive in developing scripts to load the data into the warehouse.

### Windows Instructions
1. Make sure you have a copy of Java installed on your workstation.
2. Download the latest version of the product from the community home page [http://community.pentaho.com/projects/data-integration/]([http://community.pentaho.com/projects/data-integration/)
3. The java command line settings in the provided script call for a very large heap size which is great for large jobs running on a dedicated ETL server, but probably wont start on your workstation. Download the revised [spoon.bat](https://github.com/getmovement/national-voter-file/blob/master/tools/Spoon.bat) from the tools directory on our repo and replace the script in your PDI installation directory.
4. You should be able to launch PDI by double-clicking on this new Spoon.bat in your install directory.

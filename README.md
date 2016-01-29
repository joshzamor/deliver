# OpenLMIS Module Template
This template is meant to be a starting point for developing new a new OpenLMIS 2.0 module.

## Quick Start
1. Fork/clone this repository from GitHub: [https://github.com/OpenLMIS/module-template.git](https://github.com/OpenLMIS/module-template.git)
2. Rename this repository/directory to that of your liking.  A good starting point will be the root package-name that this module will include. e.g. `org.openlmis.deliver` for a module/repository/directory name of `deliver`
3. Pull this module into OpenLMIS sub-directory `modules` using git-repo.  See our 
[default manifest repository](https://github.com/OpenLMIS/openlmis-repo) on how.
4. Write your module's code in the `src` directory.  e.g:
  ```  
  
  +-- src
  |   +-- main  
  |       +-- org
  |           +-- openlmis
  |               +-- deliver
  |   +--  test
  |        +-- org
  |            +-- openlmis
  |                +-- deliver
  ```
5. If your module depends on one or more modules, add them to `build.gradle`.  e.g. to depend on `requistion` and `stock-management`:
  ```groovy
  dependencies {
      compile project(':modules:requisition'),
      compile project(':modules:stock-management')

      testCompile project(path: ':modules:requistion', configuration: 'testFixtures'),
      testCompile project(path: ':modules:stock-management', configuration: 'testFixtures')
  }
  ```
6. If your module needs to be packaged and deployed in the WAR (which is likely):
  
  a. configure your package, dependancies, and beans in the modules applicationContext `src/main/resources/applicationContext-templateModule.xml`.  And then rename this file to the module's name, e.g. `applicationContext-deliver.xml`
  
  b. add your module as a dependancy to openlmis-web module: TODO:  stepify this or fix it with DI

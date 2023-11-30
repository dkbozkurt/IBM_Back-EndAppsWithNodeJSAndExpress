## Purpose of a package manager

Maintain a database of dependencies and versioning

Ensures software has correct dependencies

## Two main aspects of node package manager (NPM)
<ul>
<li>Provides a command line interface(CLI) to publish and download packages </li>
<li>Behaves as an online repository of JavaScript packages</li>
</ul>

## Purpose of a package.json

File located in a project`s root directory

NPM uses package.json to determine dependencies

<u>Must</u> contain <b>Project name</b> and <b>Project Version</b>

```JSON
{
    "name":"my-project",
    "version":"1.0.0"
}
```

## Local & Global install

NPM packages can be installed locally or globally.

Local install is NPM`s default behavior.

### Local install command

Use the npm cli to enter:
```
npm install <package_name>
```

This command creates a directory named <b>node_modules</b> with the package and its dependencies in your current working directory.

### Global install

A globally installed package will be used by all applications on the machine

If you have different versions of the project on your machine, they will all use the globally installed packages which might break compatibility with other dependencies.

Use the npm cli to enter
```
npm install -g <package_name>
```

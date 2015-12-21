<!--
title: 03 - npm v3
featured: true
-->

# npm v3 Dependency Resolution

## Example

Imagine we have a module, A. A requires B.

![A depends on B](/images/npm3deps1.png)

Now, let's create an application that requires module A.

On `npm install`, npm v3 will install both module A and it's
dependency, module B, inside the `/node_modules` directory, flat.

In npm v2 this would have happened in a nested way.

![npm2 vs 3](/images/npm3deps2.png)

Now let's say we want to require another module, C. C requires B,
but at another version than A.

![new module dep, C](/images/npm3deps3.png)

However, since B v1.0 is already a top-level dep, we cannot install
Bv2.0 as a top level dependency. npm v3 handles this by defaulting
to npm v2 behavior and nesting the new, different, module B version
dependency under the module that requires it, in this case, module C.

![nested dep](/images/npm3deps4.png)

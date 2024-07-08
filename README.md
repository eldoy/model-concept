# Model concept

Model concept based on mongowave.

With mongowave we can do this:

```js
var project = await db('project').get()
```

The project object is a POJO, so to update we need to do this:

```
var update = await db('project').get({ id: project.id }, { name: 'hello' })
```

Using a class or similar, we can do this to get:

```js
var project = await Project.get()
```

The `project` object is here a class instance which has functions on it, so we can do this to update:

```js
var update = await project.update({ name: 'hello' })
```

What about lists? With mongowave we do this:

```js
var projects = await db('project').find()
```

Then updates will be this:

```js
var updates = await db('project').update({}, { name: 'hello' })
```

Using classes we can do this:

```js
var projects = Project.find()
var updates = projects.update({ name: 'hello' })

// or this
Project.update({}, { name: 'hello' })
```

This requires the `projects` to be an instance of another class, `ModelList`, which behaves like an array with indexed lookup:

```js
var project = projects[0]
```

Can it just extend `Array`? Like NodeList in the browser, should be possible.

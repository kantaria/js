1. **[Что такое prototype](#JavaScript Prototype)**

## JavaScript Prototype

Прототип это тот же самый обьект, но который присутствует у родительских сущностей

```javascript
const person = {
    name: "Mikheili",
    age: 27,
    greet: function() {
      console.log("Greet");
    }
}
```
>Одно и тоже
```javascript
const person = new Object({
    name: "Mikheili",
    age: 27,
    greet: function () {
        console.log("Greet");
    }
})
```

---

#### Создание глобального прототипа

```javascript
Object.prototype.sayHello = function() {
  console.log("Hello")
}
```

---

```javascript
const person = {
    name: "Mikheili",
    age: 27,
    greet: function() {
      console.log("Greet");
    }
}

const lena = Object.create(person)
```

---

```javascript
const Person = {
	constructor: function (name, age, gender) {
		this.name = name
		this.age = age
		this.gender = gender
		return this
	},
	greet: function () {
		console.log("Hi, my name is " + this.name)
	}
}

let WebDeveloper = Object.create(Person)
WebDeveloper.constructor = function (name, age, gender, skills) {
	Person.constructor.apply(this, arguments)
	this.skills = skills || []
	return this
}
WebDeveloper.develop = function () {
	console.log("Working...")
}

let developer = Object.create(WebDeveloper).constructor("Jack", 21, "male", ["html", "css", "js"])
console.log(developer.skills);
developer.develop()
console.log(developer.name);
developer.greet()

```
>Console result
```bash
[ 'html', 'css', 'js' ]
Working...
Jack
Hi, my name is Jack
```


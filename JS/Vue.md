```html
		<div id="app">
			<p v-if="isMorning">Good morning!</p>
			<p v-if="isAfternoon">Good afternoon!</p>
			<p v-if="isEvening">Good evening!</p>
		</div>
		<script>
		var hours = new Date().getHours();
		new Vue({
			el: '#app',
			data: {
				isMorning: hours < 12,
				isAfternoon: hours >= 12 && hours < 18,
				isEvening: hours >= 18
			}
		});
		</script>
```

```html
		<div id="app">
			<p v-if="hours < 12">Good morning!</p>
			<p v-if="hours >= 12 && hours < 18">Good afternoon!</p>
			<p v-if="hours >= 18">Good evening!</p>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				hours: new Date().getHours()
			}
		});
		</script>
```

```html
		<div id="app">
			<p>Hello, {{ greetee }}!</p>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				greetee: 'world'
			}
		});
		</script>
```

```html
    <div id="app">
      <p v-if="path === '/'">You are on the home page</p>
      <p v-else>You're on {{ path }}</p>
    </div>
    <script>
    new Vue({
      el: '#app',
      data: {
        path: location.pathname
      }
    });
    </script>
```

```html
		<div id="app">
			<p>The second dog is {{ dogs[1] }}</p>
			<p>All the dogs are {{ dogs }}</p>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				dogs: ['Rex', 'Rover', 'Henrietta', 'Alan']
			}
		});
		</script>
```

#### v-if Versus v-show

You met v-if in the previous section to show and hide an element, but how does it do that, and what’s the difference between it and the similar sounding v-show? If the value of a v-if directive evaluates to falsy, the element isn’t output to the DOM.

The following Vue template 

```html
<div v-if="true">one</div>
<div v-if="false">two</div>
```

results in the following output:

```html
<div>one</div>
```


Compare that to v-show, which uses CSS to show and hide the element.

The following Vue template

```html
<div v-show="true">one</div>
<div v-show="false">two</div>
```

results in the following output:

```html
<div>one</div>
<div style="display: none">one</div>
```

First, because the inside element hidden using v-if isn’t going to be displayed, Vue doesn’t try to generate the HTML; this isn’t the case with the v-show example. This means that v-if is better for hiding stuff that hasn’t loaded yet.

```html
		<div id="app">
			<div v-show="user">
				<p>User name: {{ user.name }}</p>
			</div>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				user: undefined
			}
		});
		</script>
```

The reason the error will be thrown is that Vue has attempted to execute user.name— a property of an object that doesn’t exist. The same example using v-if works just fine, because Vue doesn’t attempt to generate the inside of the element until the v-if statement is truthy.

Also, two conditionals are related to v-if: v-else-if and v-else. They behave pretty much as you’d expect:

```html
    <div v-if="state === 'loading'">Loading…</div>
    <div v-else-if="state === 'error'">An error occurred</div>
    <div v-else>…our content!</div>
```

The first div displays if state is loading, the second if state is error, and the third if state is anything else. Only one of the elements will display at a time. OK, so having seen that, why would anyone want to use v-show?

Using v-if has a performance cost. Every time an element is added or removed, work has to be done to generate the DOM tree underneath it,

#### Looping

```html
		<div id="app">
			<ul>
				<li v-for="dog in dogs">{{ dog }}</li>
			</ul>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				dogs: ['Rex', 'Rover', 'Henrietta', 'Alan']
			}
		});
		</script>
```

```html
		<div id="app">
			<ul>
				<li v-for="(rent, city) in averageRent">
          The average rent in {{ city }} is ${{ rent }}
        </li>
			</ul>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				averageRent: {
					london: 1650,
					paris: 1730,
					NYC: 3680
				}
			}
		});
		</script>
```

```html
		<div id="app">
			<ul>
				<li v-for="n in 10">{{ n }}</li>
			</ul>
		</div>
		<script>
		new Vue({
			el: '#app'
		});
		</script>
```

#### Binding Arguments

Some directives, such as v-bind, take arguments. The v-bind directive is used to bind a value to an HTML attribute. For instance, the following example binds the value submit to the button type:

```html
		<div id="app">
			<button v-bind:type="buttonType">Test button</button>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				buttonType: 'submit'
			}
		});
		</script>
```

Will output the following code

```html
<button type="submit">Test button</button>
```

This also works with properties, such as disabled and checked: if the expression passed is truthy, the output element will have the property, and if it is falsy, the element will not:

```html
		<div id="app">
			<button v-bind:disabled="buttonDisabled">Test button</button>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				buttonDisabled: true
			}
		});
		</script>
```

When using v-bind with a lot of attributes, it can be pretty repetitive to write it out multiple times. There’s a shorter way to write it: you can omit the v-bind part of the directive and use a colon. For example, this is how you would rewrite the preceding code example using the shorter syntax:

```html
    <div id="app">
      <button :disabled="buttonDisabled">Test button</button>
    </div>
    <script>
    new Vue({
      el: '#app',
      data: {
        buttonDisabled: true
      }
    });
    </script>
```

#### Reactivity

In addition to creating the HTML in the first place, Vue watches the data object for changes and updates the DOM when the data changes.

```html
		<div id="app">
			<p>{{ seconds }} seconds have elapsed since you opened the page.</p>
		</div>
		<script>
		new Vue({
			el: '#app',
			data: {
				seconds: 0
			},
			created() {
				setInterval(() => {
					this.seconds++;
				}, 1000);
			}
		});
		</script>
```
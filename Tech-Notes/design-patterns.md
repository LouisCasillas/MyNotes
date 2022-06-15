# Design Patterns

	- Types: Creational, Management, Architectural?

	- Creational
		- How you create objects

		- Types
			- Builder
				- Simplifies the creation of objects
				- Like making a sandwich
				- Lets you call methods to build the object step-by-step 
				- Example: AlertDialog.Builder

			- Dependency Injection
				- You provide the objects that are required for the new object to work.
					- The new object doesn't need to construct or customize the objects themselves.
				- Involves 3 types of classes
					- Client class
						- Dependent class
					- Service class
						- Dependency
					- Injector class
						- Injects the service class object into the client class
				- Example: Image Loader, SharedPreferences
				- Example libraries: Dagger 2, Dagger Hilt, Koin

			- Singleton
				- Only a single instance of a class should exist.
				- In kotlin you would create a singleton object with the keyword "object".
				- Can have unintended side-effects when used by many objects as the singleton might change or get into an unexpected state.

			- Factory
					- Takes care of all the object creation logic.
					- Useful when dealing with many common objects.
					- A Factory class can get bloated due to excess objects and testing can become difficult as the Factory class is responsible for all the objects stored inside.

	- Structural
		- How you compose objects

		- Types
			- Adapter
					- Allows two incompatible classes work together by converting a class's interface into the interface the client expects.
					- Example: RecyclerView.Adapter

			- Facade
					- A higher-level interface that makes a set of other interfaces easier to use.
					- Using objects to perform complicated tasks but that provide the expected data.
					- Try to make sure the objects don't know the details of each other but just provide the data in/out expected.
					- Example: Retrofit

			- Decorator
					- Dynamically attaches additional responsibilities to an object to extend its functionality at runtime.
					- Extend object functionality by passing objects into other objects which will provide the extended functionality.

			- Composite
					- Used when you want to represent a tree-like structure consisting of uniform objects.
					- Two types of objects
							- Composite
									- Can have further objects.
							- Leaf
									- Is the last object.

	- Behavioral
		- How you coordinate object interactions

		- Types
			- Command
					- Lets you issue commands without knowing who will receive it.
					- For example: Publisher -> post() -> Event Bus -> event -> Subscriber()
					- Example: EventBus

			- Observer
					- Defines a one-to-many dependency between objects.
					- When one object changes state its dependents get a notification and update automatically.
					- Example: RxAndroid

			- Strategy
					- Multiple objects of the same nature with different functionalities.

			- State
					- The state of an object alters its behavior accordingly when the internal state of the object changes.

# Types of Project Architecture

	- MVC
		- Model View Controller
		- Steps
					1. Request sent to Controller.
					1. Controller performs logic and tells the Model what to do with the data.
					1. View takes care of what the user sees.

	- MVP
		- Model View Presenter
		- Steps
					1. User sends requests to the View.
					1. View sends message/call to Presenter.
					1. Presenter then makes request to the Model.
					1. Model returns the data to the Presenter and Presenter passes back to the View.
					1. View takes care of what the user sees.

	- MVVM
		- Model View ViewModel

	- MVI
		- Model View Intent

	- Versuses
		- MVC vs MVP
			- https://www.baeldung.com/mvc-vs-mvp-pattern
			- https://www.educba.com/mvc-vs-mvp/

		- MVP vs MVVM

		- MVC vs MVP vs MVVM
			- https://www.educba.com/mvc-vs-mvp-vs-mvvm/ 

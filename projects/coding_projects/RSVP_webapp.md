## RSVP Web Application


#### Bare minimum features
	- ability to create an rsvp for an event
	- ability to sign up for the event
	- sent a email with the event information
	- cancelation
	- edit events
	- cancel events
	- get status page for the events to see how many people sign up
	- share the event with side information

##### data objects
	- Events
		- event_id
		- Name
		- location
		- owner email
		- notes
		- number of particants
		- rsvp experation date time (optional)
		- event time and date
		- passcode=owner_email
		- Private/Public Events
	- particapent
		- particapation_id
		- name
		- particapent email
		- event_id

#### UI

##### Pages
	- Home
		- Plus button to create an event
			- Popup form for creating the event
		- List of 10 public event happening now 
	- Events Page /{event}
		- Event information
		- Sign up form
		- Edit with passcode
			- Pulls up and edit window
				- Notes
				- RSVP experation 
				- event time and date
				- private/public status
			- Enable a delete feature
	- Paticapation /{particapation id}
		- Their linked event detials
		- Paticipation information


##### API
	- Events endpoint
		- Create Events
		- Update Events details
		- Remove Events
	- Paticapent
		- Create RSVP signup
		- Remove RSVP signup
		


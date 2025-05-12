# 🗓️ Daily
template:: Daily
template-including-parent:: false
	- ## 🕰️ Reminders
	  collapsed:: true
		- ### Tasks For Today
		  query-table:: false
		  collapsed:: true
		  {{query (task todo doing now later wait)}}
		-
		- ### Important Events
		  query-table:: true
		  query-properties:: [:start-time :end-time :event-name :date]
		  collapsed:: true
		  {{query (and [[Important Events]] (not (page [[Important Events]])) (not (page [[templates]])))}}
		-
	- ## 📋 Todo List
	  collapsed:: true
		- :LOGBOOK:
		  CLOCK: [2025-05-02 Fri 17:49:04]
		  :END:
	- ##  ✏️ Summary
	  collapsed:: true
		- Today was a...
	- ## 🗒️ Pages
	- ## 🗓️ Important Events
		- query-table:: true
		  query-properties:: [:start-time :end-time :event-name :date]
		-
		-
		-
		-
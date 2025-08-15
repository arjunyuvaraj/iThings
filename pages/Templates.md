icon:: 📝

- # 🗓️ Daily
  template:: Daily
  template-including-parent:: false
	- ## 🕰️ Reminders
	  collapsed:: true
		- ### Tasks For Today
		  query-table:: true
		  {{query (task todo doing now later wait)}}
	- ## 📋 Todo List
	  collapsed:: true
		- :LOGBOOK:
		  CLOCK: [2025-05-02 Fri 17:49:04]
		  :END:
	- ##  ✏️ Summary
	  collapsed:: true
		- Today was a...
	- ## 🗒️ Pages
	- ## [[Important Events]]
- template:: book review
	- {{title}}
	  type:: book
	  cover:: {{thumbnail}}
	  authors:: {{authors}}
	  published:: {{publishedAt}}
	  isbn:: {{isbn}}
	  categories:: {{categories}}
	  pages:: {{pages}}
	  language:: {{language}}
	  publisher:: {{publisher}}
	  maturity:: {{maturityRating}}
	  description:: {{description}}
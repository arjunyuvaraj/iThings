icon:: 📝

- # 🗓️ Daily
  template:: Daily
  template-including-parent:: false
  collapsed:: true
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
- book card temp
  template:: template-book-card
  collapsed:: true
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
- template:: properties
  description:: An example of how to retrieve properties values
	- from template itself: ``c.template.props.description``
	- from current block: ``c.self.props.message``
	  message:: hello!
	- from the page, the second tag: ``c.page.propsRefs.tags[1]``
	- and from the destination block: ``c.block.props.info``
	-
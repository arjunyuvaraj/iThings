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
- template:: glass-card
  template-version:: 11
  plugin-version:: 4.0.0
  link:: [Shiny `Glass Card` from Logseq landing page](https://github.com/stdword/logseq13-full-house-plugin/discussions/9)
  template-list-as:: view
  template-usage:: `:page [[{|}]]`
  arg-cover::
  arg-title:: .name
  arg-info1:: @author
  arg-info2:: @category
  arg-info3::
  arg-card-width::
  arg-cover-height::
  arg-cover-width:: 56px
	- ```jsx
	  <style>
	    #``c.identity.slot`` .glass-card {
	      background-image: linear-gradient(
	        to right bottom,
	        var(--gradient-from),
	        55%,
	        var(--gradient-to)
	      );
	      --gradient-from: color-mix(
	        in srgb,
	        var(--ls-selection-text-color) 25%,
	        transparent
	      );
	      --gradient-to: color-mix(
	        in srgb,
	        var(--ls-primary-background-color) 10%,
	        transparent
	      );
	      border-radius: 0.5rem;
	      backdrop-filter: blur(30px); /* reduce blur for performance */
	    }
	  
	    #``c.identity.slot`` .glass-card > div {
	      background-color: color-mix(
	        in srgb,
	        var(--ls-primary-background-color) 60%,
	        transparent
	      );
	      border-radius: 0.5rem;
	      margin: 0.5px;
	      padding: 15px 0.75rem 0.75rem;
	      ``when(c.args['card-width'], 'min-width: $1;')``
	      ``when(c.args['card-width'], 'max-width: $1;')``
	    }
	  
	    #``c.identity.slot`` .glass-card > div > div {
	      height: auto !important;
	    }
	  
	    #``c.identity.slot`` .glass-card img {
	      ``when(c.args['cover-width'], 'width: $1; min-width: $1;')``
	      ``when(c.args['cover-height'], 'height: $1; min-height: $1;')``
	    }
	  
	    #``c.identity.slot`` .glass-card div > a > strong {
	      color: color-mix(
	        in srgb,
	        var(--ls-link-text-hover-color) 90%,
	        var(--ls-body-font-color) 10%
	      );
	    }
	  
	    #``c.identity.slot`` .glass-card .info {
	      font-size: 0.9rem;
	      font-weight: 300;
	      line-height: 1.5rem;
	      color: var(--ls-body-font-color);
	    }
	  
	    /* Optional: subtle border for dark themes */
	    @media (prefers-color-scheme: dark) {
	      #``c.identity.slot`` .glass-card {
	        border: 1px solid rgba(255, 255, 255, 0.1);
	      }
	    }
	  </style>
	  
	  ```
	-
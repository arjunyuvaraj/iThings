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
- collapsed:: true
-
-
-
-
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
  arg-info3:: @rating
  arg-info4:: @recommend
  arg-card-width:: 
  arg-cover-height::
  arg-cover-width::
	- ```jsx
	  <style>
	    #``c.identity.slot`` .glass-card {
	      display: grid;
	      grid-template-columns: 120px 1fr;  /* left: cover, right: text */
	      grid-template-rows: auto auto auto auto; /* title + 3 rows of info */
	      width: 100%;
	      box-sizing: border-box;
	      margin: 8px 0;
	      border-radius: 0.5rem;
	      backdrop-filter: blur(100px);
	      overflow: hidden;
	      padding: 12px;
	      background-color: color-mix(in srgb, var(--ls-primary-background-color) 50%, transparent);
	      gap: 6px;
	      align-items: start;
	    }
	  
	    #``c.identity.slot`` .glass-card img {
	      grid-row: 1 / span 4;  /* cover spans all rows on left */
	      width: 100%;
	      height: auto;
	      border-radius: 0.4rem;
	      object-fit: cover;
	    }
	  
	    #``c.identity.slot`` .glass-card .title {
	      grid-column: 2;
	      font-size: 1.3rem;
	      font-weight: 600;
	    }
	  
	    #``c.identity.slot`` .glass-card .field {
	      grid-column: 2;
	      font-size: 0.9rem;
	    }
	  
	    #``c.identity.slot`` .glass-card .label {
	      font-weight: 600;
	      margin-right: 4px;
	    }
	  </style>
	  ``{_
	      var mode = c.args.block ? 'block' : 'page'
	      var reference = mode === 'block' ? c.block.uuid : c.page.name_
	      
	      var title = when(c.args.title, dev.get(mode + c.args.title) || c.args.title)
	      var info1 = when(c.args.info1, dev.get(mode + c.args.info1) || c.args.info1)
	      var info2 = when(c.args.info2, dev.get(mode + c.args.info2) || c.args.info2)
	      var info3 = when(c.args.info3, dev.get(mode + c.args.info3) || c.args.info3)
	      var info4 = when(c.args.info4, dev.get(mode + c.args.info4) || c.args.info4)
	      
	      if (title) {
	          if (Array.isArray(title))
	              title = title[0]
	          if (title.startsWith('[[') && title.endsWith(']]'))
	              title = title.slice(2, -2)
	      }
	      if (info1) {
	          info1 = Array.isArray(info1) ? info1 : [info1]
	        info1 = dev.toHTML(info1.join('\n'))
	      }
	      if (info2) {
	          info2 = Array.isArray(info2) ? info2 : [info2]
	        info2 = dev.toHTML(info2.join('\n'))
	      }
	      if (info3) {
	         info3 = Array.isArray(info3) ? info3 : [info3]
	         info3 = dev.toHTML(info3.join('\n'))
	      }
	      if (info4) {
	         info4 = Array.isArray(info4) ? info4 : [info4]
	         info4 = dev.toHTML(info4.join('\n'))
	      }
	  
	      var markup
	      if (!c.args.cover && mode === 'page') {
	          const tree = top.logseq.api.get_page_blocks_tree(c.page.name)
	          markup = tree[0].children[0].content
	          if (!markup)
	            markup = tree[1].content
	      }
	      else
	          markup = when(c.args.cover, dev.get(mode + c.args.cover) || c.args.cover)
	  
	        var cover = ''
	      if (markup) {
	        [ cover ] = dev.links(markup)
	        if (!cover)
	                cover = dev.asset(markup)
	      }
	  _}``
	  <div class="glass-card">
	    ``{_ if (cover) { _}``
	      <a data-on-click="clickRef" data-ref="``reference``">
	        <img src="``cover``"
	          ``_ when(c.args['cover-width'], 'width="$1"') _``
	          ``_ when(c.args['cover-height'], 'height="$1"') _``
	        />
	      </a>
	    ``{ } _}``
	  
	    ``{_ if (title) { _}``
	      <div class="title">
	        <a data-on-click="clickRef" data-ref="``reference``">``title``</a>
	      </div>
	    ``{ } _}``
	  
	    <div class="field"><strong class="label">Author:</strong> ``_ when(info1, '$1') _``</div>
	    <div class="field"><strong class="label">Rating:</strong> ``_ when(info3, '$1') _``</div>
	    <div class="field"><strong class="label">Category:</strong> ``_ when(info2, '$1') _``</div>
	    <div class="field"><strong class="label">Recommend:</strong> ``_ when(info4, '$1') _``</div>
	  </div>
	  
	  
	  ```
-
	- ```jsx
	  <style>
	    #``c.identity.slot`` .glass-card {
	      background-image: linear-gradient(to right bottom, var(--gradient-from), 25%, var(--gradient-to));
	      --gradient-from: color-mix(in srgb, var(--ls-primary-background-color) 35%, white);
	      --gradient-to: color-mix(in srgb, var(--ls-primary-background-color) 10%, transparent);
	      border-radius: 0.5rem;
	      backdrop-filter: blur(100px);
	    }
	  
	    #``c.identity.slot`` .glass-card > div {
	      background-color: color-mix(in srgb, var(--ls-primary-background-color) 50%, transparent);
	      border-radius: 0.5rem;
	      margin: 0.5px;
	      padding: 15px 0.75rem 0.75rem;
	      ``when(c.args['card-width'], 'min-width: $1;')``
	      ``when(c.args['card-width'], 'max-width: $1;')``
	    }
	  
	    #``c.identity.slot`` .glass-card > div > div {
	      /* compatibility with Bullet Threading plugin */
	      height: auto !important;
	    }
	  
	    #``c.identity.slot`` .glass-card img {
	      ``when(c.args['cover-width'], 'width: $1; min-width: $1;')``
	      ``when(c.args['cover-height'], 'height: $1; min-height: $1;')``
	    }
	  
	    #``c.identity.slot`` .glass-card div > a > strong {
	      color: color-mix(in srgb, var(--ls-link-text-hover-color) 80%, transparent);
	    }
	  
	    #``c.identity.slot`` .glass-card .info {
	      font-size: 0.9rem;
	      font-weight: 300;
	      line-height: 1.5rem;
	    }
	  </style>
	  
	  ``{_
	      var mode = c.args.block ? 'block' : 'page'
	      var reference = mode === 'block' ? c.block.uuid : c.page.name_
	      
	      var title = when(c.args.title, dev.get(mode + c.args.title) || c.args.title)
	      var info1 = when(c.args.info1, dev.get(mode + c.args.info1) || c.args.info1)
	      var info2 = when(c.args.info2, dev.get(mode + c.args.info2) || c.args.info2)
	      var info3 = when(c.args.info3, dev.get(mode + c.args.info3) || c.args.info3)
	      
	      if (title) {
	          if (Array.isArray(title))
	              title = title[0]
	          if (title.startsWith('[[') && title.endsWith(']]'))
	              title = title.slice(2, -2)
	      }
	      if (info1) {
	          info1 = Array.isArray(info1) ? info1 : [info1]
	        info1 = dev.toHTML(info1.join('\n'))
	      }
	      if (info2) {
	          info2 = Array.isArray(info2) ? info2 : [info2]
	        info2 = dev.toHTML(info2.join('\n'))
	      }
	     if (info3) {
	          info3 = Array.isArray(info3) ? info3 : [info3]
	        info3 = dev.toHTML(info3.join('\n'))
	      }
	  
	      var markup
	      if (!c.args.cover && mode === 'page') {
	          const tree = top.logseq.api.get_page_blocks_tree(c.page.name)
	          markup = tree[0].children[0].content
	          if (!markup)
	            markup = tree[1].content
	      }
	      else
	          markup = when(c.args.cover, dev.get(mode + c.args.cover) || c.args.cover)
	  
	        var cover = ''
	      if (markup) {
	        [ cover ] = dev.links(markup)
	        if (!cover)
	                cover = dev.asset(markup)
	      }
	  _}``
	  
	  <div class="glass-card">
	      <div class="flex">
	          <div class="flex items-center">
	              <a data-on-click="clickRef" data-ref="``reference``">
	                    ``{_ if (cover) {   _}``
	                    <img src="``cover``"
	                    ``_ when(c.args['cover-width'], 'width="$1"') _``
	                    ``_ when(c.args['cover-height'], 'height="$1"') _``
	                    />``{ }   _}``
	              </a>
	          </div>
	          ``{_ if (title || info1 || info2 || info3) {   _}``
	              <div class="info flex-col px-3 opacity-80">
	                  ``{_ if (title) {  _}``
	                      <a data-on-click="clickRef" data-ref="``reference``">
	                          <strong class="text-2xl font-medium">``title``</strong></a>``{ }   _}``
	                      ``_ when(info1, '<div class="pt-2 pb-1">$1</div>') _``
	                      ``_ when(info2, '<div class="pt-1 pb-1">$1</div>') _``
	                      ``_ when(info3, '<div class="pt-2"     >$1</div>') _``
	                      ``_ when(info4, '<div class="pt-1"     >$1</div>') _``
	              </div>``{ }   _}``
	    </div>
	  </div>
	  ```
	-
-
-
-
-
-
-
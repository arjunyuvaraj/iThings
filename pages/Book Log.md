icon:: 📚
subject:: Reading, Books, English
banner:: https://images.unsplash.com/photo-1479142506502-19b3a3b7ff33?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D

- ```jsx
  <style>
    #``c.identity.slot`` .glass-card {
      background-image: linear-gradient(to right bottom, var(--gradient-from), 55%, var(--gradient-to));
      --gradient-from: color-mix(in srgb, var(--ls-selection-text-color) 35%, transparent);
      --gradient-to: color-mix(in srgb, var(--color-level-6) 10%, transparent);
      border-radius: 0.5rem;
      // backdrop-filter: blur(100px);
    }
  
    #``c.identity.slot`` .glass-card > div {
      background-color: color-mix(in srgb, var(--ls-primary-background-color) 50%, transparent);
      border-radius: 0.5rem;
      border: 1px, solid, white;
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
              </div>``{ }   _}``
    </div>
  </div>
-
-
-
-
-
-
-
-
-
-
-
- ## To Be Read
  collapsed:: true
	- |**Title**|**Author**|**Rating**|**Recommend**|
	  |--|--|--|--|
	  |Caraval|Stephanie Garber| - | - |
	  |Long Way Down|Jason Reynolds| - | - |
	  |Wicked: The Wicked Witch of the West|Gregory Maguire| - | - |
	  |Son of a Witch|Gregory Maguire| - | - |
	  |Lion Among Men|Gregory Maguire| - | - |
	  |Out of Oz|Gregory Maguire| - | - |
	-
	-
- ## Favorite Books
  collapsed:: true
	- The Book Thief by Markus Zusak
	  logseq.order-list-type:: number
	- A List of Cages by Robin Reul
	  logseq.order-list-type:: number
	- The Naturals by Jennifer Lynn Barnes
	  logseq.order-list-type:: number
	- Run with the Wind by Shion Miura
	  logseq.order-list-type:: number
	- This is Our Story by Ashley Elston
	  logseq.order-list-type:: number
	- Where the Road Leads Us by Robin Reul
	  logseq.order-list-type:: number
- ## June 2025
	- **Lost in the Sun** by Lisa Graff
		- {{Lost in the Wind}}
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
		- {{renderer :full-house, template-book-card, title=Lost in the Sun, authors=Lisa Colleen Graff, publishedAt=12/31/2014, isbn=0399164065, categories=Juvenile Nonfiction / Social Topics / Dating & Relationships, Juvenile Fiction / Family / General, Juvenile Fiction / Family / Marriage & Divorce, Juvenile Fiction / Family / Siblings, Juvenile Fiction / Social Themes / Emotions & Feelings, Juvenile Fiction / Social Themes / Friendship, pages=289, language=en, publisher=Penguin, maturityRating=NOT_MATURE, description=<b>From the author of <i>A Tangle of Knots</i> and <i>Absolutely Almost</i>, a touching story about a boy who won't let one tragic accident define him.</b><br> <br> Everyone says that middle school is awful, but Trent knows nothing could be worse than the year he had in fifth grade, when a freak accident on Cedar Lake left one kid dead, and Trent with a brain full of terrible thoughts he can't get rid of. Trent's pretty positive the entire disaster was his fault, so for him middle school feels like a fresh start, a chance to prove to everyone that he's not the horrible screw-up they seem to think he is. <br> <br> If only Trent could make that fresh start <i>happen.<br></i> <br> It isn't until Trent gets caught up in the whirlwind that is Fallon Little--the girl with the mysterious scar across her face--that things begin to change. Because fresh starts aren't always easy. Even in baseball, when a fly ball gets lost in the sun, you have to remember to shift your position to find it.<br> <br> <b>Praise for <i>Lost in the Sun</i>:</b><br> <br> A <i>Publishers Weekly</i> Best Book of the Year!<br> <br> <b>*</b> "Graff writes with stunning insight [and] consistently demonstrates why character-driven novels can live from generation to generation."--<i>Kirkus Reviews</i> *STARRED*<br> <br> <b>*</b> "Graff creates layered, vulnerable characters that are worth getting to know."--<i>Booklist </i>*STARRED*<br> <br> <b>*</b> "[A]n ambitious and gracefully executed story."--<i>Publishers Weekly</i> *STARRED*<br> <br> <b>*</b> "Weighty matters deftly handled with humor and grace will give this book wide appeal."--<i>School Library Journal</i> *STARRED*<br> <br> <b>*</b> "Characterization is thoughtful."--<i>BCCB</i> *STARRED*<br> <br> "In <i>Lost in the Sun</i>, Trent decides that he will speak the truth: that pain and anger and loss are not the final words, that goodness can find us after all--even when we hide from it. This is a novel that speaks powerfully, honestly, almost shockingly about our human pain and our human redemption. This book will change you."--Gary Schmidt, two-time Newbery Honor-winning author of <i>The Wednesday Wars </i>and <i>Lizzie Bright and the Buckminster Boy</i><br> <br> "Lisa Graff crafts a compelling story about a boy touched with tragedy and the world of people he cares about. And like all the best stories, it ends at a new beginning."--Richard Peck, Newbery Award-winning author of <i>A Year Down Yonder</i> and <i>A Long Way From Chicago</i><br> <br> <br> <b>Lisa Graff's Awards and Reviews:</b><br> <br> Lisa Graff's books have been named to 30 state award lists, and <i>A Tangle of Knots </i>was long-listed for the National Book Award., thumbnail=http://books.google.com/books/publisher/content?id=PEmLDQAAQBAJ&printsec=frontcover&img=1&zoom=1&edge=curl&imgtk=AFLRE73V1jqwLksxl4cNvFPyuebm0pZDVM6-CG5jHtziWw4SLI1blWVLxVrRQMHYeOd249joH3k9jw9l1Z7TZWlZmd-T8niNkvH5phhEn5_gToLmSS_arjx4G7zxPJp6jLodn-3xhM_6&source=gbs_api }} 
		  collapsed:: true
		  :LOGBOOK:
		  CLOCK: [2025-08-15 Fri 19:12:41]--[2025-08-15 Fri 19:12:42] =>  00:00:01
		  :END:
			-
			-
	- **ISBN:** 0399164065
		-
	- |**Title**|**Author**|**Rating**|**Recommend**|
	  |--|--|--|--|
	  |Lost in the Sun|Lisa Graff|7.4/10|3.5/5|
	  |Where the Road Leads Us|Robin Reul|9.5/10|5/5|
	  |This Is Our Story|Ashley Elston|8.5/10|4.5/5|
	  |Kings of the Wyld|Nicholas Eames|5/10|2.5/5|
	  |Patron Saints of Nothing|Randy Ribay|8.7/10|4.5/5|
- ## July 2025
  collapsed:: true
	- |**Title**|**Author**|**Rating**|**Recommend**|
	  |--|--|--|--|
	  |The Naturals|Jennifer Lynn Barnes|9.5/10|4/5|
	  |The Naturals: Killer Instinct|Jennifer Lynn Barnes|9.3/10|4/5|
	  |The Naturals: All In|Jennifer Lynn Barnes|9.7/10|4/5|
	  |The Naturals: Bad Blood|Jennifer Lynn Barnes|9.5/10|4/5|
	  |The Naturals: Twelve|Jennifer Lynn Barnes|6.5/10|2.5/5|
	  |The Book of Doors|Gareth Brown|9.0/10|4.5/5|
	  |The School for Good and Evil|Soman Chainani|6.5/10|2.5/5|
	  |A World Without Princes|Soman Chainani|6.5/10|2.5/5|
	  |The Last Ever After|Soman Chainani|6.5/10|2.5/5|
- ## August 2025
  collapsed:: true
	- |**Title**|**Author**|**Rating**|**Recommend**|
	  |--|--|--|--|
	  |Quests for Glory|Soman Chainani|7/10|2.5/5|
	  |A Crystal Of Time|Soman Chainani|8.5/10|2.5/5|
	  |One True King|Soman Chainani|8.7/10|2.5/5|
	  |Long Way Down|Jason Reynolds|4.5/10|2.5/5|
	  |Run With The Wind|Shion Miura|9.5/10|5/5|
	  |Ready Player One|Ernest Cline|7.5/10|4.5/5|
	- https://www.google.com
	-
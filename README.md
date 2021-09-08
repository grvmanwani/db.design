# DB DESIGN RDBMS
# gaurav manwani

Design a database structure for below use case –
I have an ecommerce platform. I have a wide range of catalog (products) having many attributes
for each. I want to build a page like Amazon’s Today’s Deal (https://www.amazon.in/gp/goldbox).


	Master Data Table 'categories'	 :  	id(BIGINT)
						, name(VARCHAR)
						, active(TINYINT)
						, created_at(BIGINT)
						, updated_at(BIGINT)
						
	Master Data Table 'color'	 :  	id(BIGINT)
						, name(VARCHAR)
						, active(TINYINT)
						, created_at(BIGINT)
						, updated_at(BIGINT)
		    
	TABLE 'item_details' 		 :  	id(BIGINT)
		    				, name(VARCHAR)
						, price(BIGINT)
						, category(BIGINT). fk_categories
						, active(TINYINT)
						, created_at(BIGINT)
						, updated_at(BIGINT)
						
	TABLE 'item_color_details'	  : 	id(BIGINT)
		    				, item_id(BIGINT) fk_item
						, color_id(BIGINT) fk_color
						, active(TINYINT)
						, created_at(BIGINT)
						, updated_at(BIGINT)
	
	//TABLE FOR Today's Deals like (https://www.amazon.in/gp/goldbox).
	Table 'current_deals'		  :  	id(BIGINT)
						, item_id(BIGINT) FK_item 
						, status(INT). // 1.AVAILABLE 2.UPCOMMING 3.MISSED
						, active(TINYINT). //0.NOT ACTIVE, 1.ACTIVE
						, created_at(BIGINT)
						, updated_at(BIGINT)

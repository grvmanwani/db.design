# interview.bewkoof.com
# gaurav manwani

Q1. You have a list of strings. Write a function to add a string to the list and another function
to find the strings which are kth most repeated in the list.


//PYHTON SOLUTION.

class Solution(object):
	words=[]
	
    def addToList(str):
	words.append(str)

    def topKFrequent(self, words, k):
        count = collections.Counter(words)
        data = count.keys()
        data.sort(key = lambda w: (-count[w], w))
        return data[k-1:k]
	
	
//JAVA SOLUTION.

public class Test {
    List<String> words=new ArrayList<>();

    private void addToList(String str){
        words.add(str.trim());
    }

    public String kthMostFrequent(int k) {
        HashMap<String, Integer> map = new HashMap<>();

        for (String s : words) {
            Integer x = map.get(s);
            if (x == null) x = 0;
            map.put(s, ++x);
        }

        List<Map.Entry> list = new ArrayList(map.entrySet());

        Collections.sort(list, new Comparator<Object>() {
            public int compare(Object o1, Object o2) {
                Integer v1 = (Integer) ((Map.Entry) o1).getValue();
                Integer v2 = (Integer) ((Map.Entry) o2).getValue();
                return v1.compareTo(v2);
            }
        });

        if (list.size() > k) return (String) (list.get(k)).getKey();
        return null;
    }
}


Q.2 Design a database structure for below use case –
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

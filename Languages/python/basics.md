print(), prints some thing to the screen
dict, this is like a hash map in c++ or something else. This is used to create 


count =0
for i in orders:
    if 'state' in i and i['state'] == "CA":
        print(i)
        count = count +1
print (count)  
print("\n")
print("There are {} orders from CA")


Create a list `high_value_order_ids` containing `order_id` for orders where `unit_price * quantity >= 500`.

- Print the number of such orders.

high_value_order_ids = []
number =0
for i in orders:
	a = i['unit_price']
	b = i['quantity']

	if a*b >= 500:
		number += 1
print("There are"+str(number)+" orders that are high value, given that the product of the unit price and quantity of the order is at least 500 or greater.")


`my_dict = {'name': 'Alice', 'age': 30, 'city': 'NY'} for key, value in my_dict.items():     print(f"{key}: {value}")`

for i in range(3):
    print(orders[i])
    print("\n")
	for key,value in i.items():
		print("{key}: {value}\n")

2.1:
	given an order, return the product unit_price and quantity.
	GIven an order, return the total price of the order after its discount found by the formula, total = subtotal * (1 -discount_pct/100). Now if this discount_pct is invalid either over 50 or under 0, treat it as 0. 
		alright so here it is 
		sub = order_subtotal(order)
		dis = order['discount_pct']
		total = sub (1- (dis/100))
		return total
	Given an variable called x, convert it into a float type, if not rteturn None.
to type cast in python, you can jsut use the build in functions, like int(), float(),str(), etc


alright to handle errors you can use try and except.
whatever code is run in the try block, if it raises an error of any kind, then the code in the except block will be executed.

count=[]
for i in orders:
	j=i+1
	count.append(j)
for i in range(5):
	random.choice(count)
	value:.2f


clean_discount_pct(order):
	try:
		 order['discount_pct']
	except:
		print(f"Error with {order} discount_pct field")
		return None
	a = order['discount_pct']
	if a > 50:
		a =50
	return a
import datetime as dt
parse_date(date_str):
	//returns a date time .date or None if invalid
	try:
		return parsed_date = datetime.strptime(date_str, '%Y-%m-%d).date()
	except:
		print("error turning string into a date")
		return None
Clean_ratings(x)
	// returns float rating in [1,5]] if valid or none if missing or N/A
	a = safe_float(x)
	if a is None:
		return a
	return a 

Create a new list clean_orders whre each order: has a order_date_obj(parsed date), has discount_pct_clean, and has rating_clean.
Do Not Delete any rows yet.

print how many orders have invalid dates and how many have missing/invalid ratings

to 'rename', a key you can .pop the old value which returns the value assocaited with it, and then deletes the key-value pair. this allows you to add

bad_date =0
invalid_rating=0
for i in orders:
count =0
	if parse_date(i['order_date']):
		i['order_date'] = parse_date(i['order_date'])
		i['order_date_obj']=i.pop('order_date')
		count +=1
	elif parse_date(i['order_date']) is None:
		bad_date +=1
	elif clean_discount_pct(i):
		i['discount_pct']= clean_discount_pct(i[discount_pct])
		i['discount_pct_clean']= i.pop('discount_pct')
		count+=1
	elif clean_rating(i['rating']):
		i['rating']= clean_rating.(i['rating'])
		i['rating_clean'] = i.pop('rating')
		count+=1
	elif clean_rating(i['rating']) is None:
		invalid_rating +=1
	elif count  is 3:
		clean_orders.append(i)
	order_date y, m ,d

def parse_date(date_str):
    # TODO

	if not date_str:
		return None
    try:
        a = dt.strptime(date_str.strip(), '%Y-%m-%d').date()
        return a
    except ValueError:
        print("error turning provided string into a date")
        return None
    error turning provided string into a date
{'order_id': 10002, 'customer_id': 2113, 'order_date': '2025-12-01', 'state': 'CO', 'category': 'Clothing', 'payment': 'card', 'unit_price': 133.18, 'quantity': 1, 'discount_pct': 10, 'shipping_days': 6, 'returned': False, 'rating': 3.7}
None

Okay so this code
for i in orders:
	count=0
	if parse_date(i['order_date']):
	i['order_date'] = parse_date(i['order_date'])         i['order_date_obj']= i.pop('order_date')
raises an error, key error, as if the code tries to access that particular key and if it isnt there, then the error is raised and the code stops.

so despite having some small kind of error handling within the function, it still needs to be handled here. This could be handled with `if key is not in i:` as this would continue the code despite the key not being in the dict.
so lets try this.

if "order_date" is not in i:
	bad_date+=1

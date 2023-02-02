# parkingSlots
- use Laravel Framework 9.49.0
- use mysql as database


1. Run the database migration

2. insert data to the slot table

	$slots=new Slots(); 
        $SlotName=Array("A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","D"); 
        $j=1;
        foreach($SlotName as $key=>$val){
                for($i=1;$i<=5;$i++){                    
                    $slots=new Slots();
                    $slots->slot_number= $j;
                    $slots->slot_name=$val.sprintf("%02d", $i);
                    $slots->status=false;
                    $slots->save();
                    $j++;
                }
        }

To Execute The program.
-----------------------
To get the customer List and total fee

1. http://127.0.0.1:8000/customerList

To get the upcomming list and total fee
2. http://127.0.0.1:8000/upcomingList

3 . Book parking API call
http://127.0.0.1:8000/api/bookParking

sample call 

	curl --location --request POST 'http://127.0.0.1:8000/api/bookParking' \
--form 'file=@"/home/ajith/Downloads/eStatement.pdf"' \
--form 'data="{\"customer_name\":\"Renju\",\"phone_number\":\"9876543245\",\"vehicle_number\":\"KL4234\"}"'

4. Checkout API call
http://127.0.0.1:8000/api/checkoutParking

sample call 

curl --location --request POST 'http://127.0.0.1:8000/api/checkoutParking?parkingId=15'


Controllers used :- HomeController

Models :- Customer , Parking , Slots

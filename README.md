
  # maximum trigger depth exceeded
 ### This important aspect of using a trigger (after update) when updating the same trigger object.
when we wirte trigger after update to updating the same trigger object.

we shound be use 
```jsx
public class opp {
    
    public static Boolean isTriggerExecuted = false;

    public static void amount(list<Opportunity> opplist){
        if(isTriggerExecuted){
            return;
        }
        isTriggerExecuted = True;
       
         // logic here
                   
    }  
        isTriggerExecuted = false;
}
         
}
```

# logic here


```jsx
set<id> AccountID =new Set<id>();
for(opportunity opp:[Select id,AccountId,Total_Opportunity_Amount__c From opportunity Where AccountID !=null]){
    
    AccountID.add(opp.AccountId);
    
}
 map<id,Decimal> updateamount=new map<id,Decimal>(); 
for(AggregateResult Result:[Select AccountID,Sum(Amount)total From opportunity Where AccountId in: AccountID Group by AccountId]){
     
    updateamount.put((id)Result.get('AccountID'),(Decimal)Result.get('total'));
    
    
}
list<opportunity>  opport=new list<opportunity>();
for(opportunity opp:[Select id,AccountId,Total_Opportunity_Amount__c From opportunity Where AccountID !=null]){
    
    if(updateamount.containsKey(opp.AccountId)){
           opp.Total_Opportunity_Amount__c=updateamount.get(opp.AccountId);
           
    }
     opport.add(opp);
    
}


if(!opport.isEmpty()){
 
    update opport;

}
```

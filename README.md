 # This important aspect of using a trigger (after update) when updating the same trigger object.
when we wirte trigger after update to updating the same trigger object.

we shound be use 

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

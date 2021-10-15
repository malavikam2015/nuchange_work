# nuchange_work
#java_program
package placement;
import java.util.*;
import java.lang.*;
public class UrlDataBase {
 static boolean check(Url[] url,String link,int i) {
  for(int a=0;a<i;a++) {
   if(link.equals(url[a].urlLink)) {
    return true;
   }
  }
  return false;
 }
 public static void main(String args[]) {
   
  Scanner s=new Scanner(System.in);
  Url[] url = new Url[10];
  boolean run = true;
  int i = 0;
  while(run == true) {
   System.out.print("Enter Command > ");
   String str = s.nextLine();
   String cmd;
   String link = null;
   try {
    String[] commands = str.split(" ");
    cmd = commands[0];
    link = commands[1];
   }catch(java.lang.ArrayIndexOutOfBoundsException e) {
    cmd = str;
   }
   switch(cmd) {
   case "get":
    for(int a=0;a<i;a++) {
     if(link.equals(url[a].urlLink)) {
      url[a].count++;
      System.out.println("ID : "+url[a].id);
      System.out.println("Count : "+url[a].count);
     }
    }
    break;
   case "store":
    if(check(url,link,i)) {
     System.out.println("Already Exist");
     break;
    }
    url[i] = new Url();
    url[i].urlLink = link;
    url[i].id = UUID.randomUUID();
    i++;
    break;
   case "list":
    for(int j=0;j<i;j++) {
     System.out.println(url[j].id+"  "+url[j].urlLink+"  "+url[j].count);
    }
    break;
   case "count":
    for(int a=0;a<i;a++) {
     if(link.equals(url[a].urlLink)) {
      System.out.println("Count : "+url[a].count);
     }
    }
    break;
   case "exit":
    run = false;
    System.out.println("Terminated");
    break;
   default:
    System.out.println("Enter a valid command");
    break;
   }
  }
 }
}
class Url{
 public UUID id;
 public String urlLink;
 public int count = 0;
}


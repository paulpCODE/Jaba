import java.util.Scanner;
import java.util.ArrayList;
import java.util.Arrays;

class House{
    private String m_houseName;
    private int m_sum;
    private ArrayList<Integer> m_Number;
    private boolean m_isOpened;
    
    public boolean getIsOpened() {
        return m_isOpened;
    }
    
    public int getSum() {
        return m_sum;
    }
    
    public String getName() {
        return m_houseName;
    }
    
    public ArrayList<Integer> getNumber() {
        return m_Number;
    }
    
    public void setSum(int sum) {
        m_sum = sum;
    }
    
    public void SetOpened(boolean isOpened) {
        m_isOpened = isOpened;
    }
    
    public void printHouse(){
          System.out.print(m_houseName +"("+ "Sum: " + m_sum + ")" + " : " );
          for (int i = 0; i<m_Number.size();i++){
               System.out.print(m_Number.get(i) + " ");
               
          }
           System.out.println();
    }
    
    public House(String name){
        m_sum = 0;
        m_houseName = name;
        m_Number = new ArrayList(); 
        m_isOpened = true;
    }
    
  
}

class Player {
    private String m_name;
    private boolean m_turn;
    private int m_score;
    public Player(boolean turn) {
        m_score = 0;
        if(turn) {
            m_name = "WHITE";
            m_turn = true;
        } else {
            m_name = "BLACK";
            m_turn = false;
        }
    }
    
    public boolean getTurn() {
        return m_turn;
    } 
    public int getScore() {
        return m_score;
    }
    public String getName() {
        return m_name;
    }
    public void setScore(int score) {
        m_score = score;
    }
    public void setTurn(boolean t) {
        m_turn = t;
    }
    
}
public class Main
{
   public static void main(String args[]) {
          //Scanner in = new Scanner(System.in);
          ArrayList<House> myHouses = new ArrayList<>();
          for(int i = 0; i < 4; i++) {
              myHouses.add(new House("H" + (i + 1)));
          }
          Player PlayerWhite = new Player(true);
          Player PlayerBlack = new Player(false);
          Player currentPlayer = new Player(true);
          
          while(isGameContinue(myHouses)) {
              int randScoreNum = randomNumber();
              if(PlayerWhite.getTurn() == true) { //Если ход белого то текущий игрок белый и меняем ходы местами
                  currentPlayer = PlayerWhite;
                  PlayerWhite.setTurn(false);
                  PlayerBlack.setTurn(true);
             }
             else { //Зеркально
                 currentPlayer = PlayerBlack;
                 PlayerWhite.setTurn(true);
                  PlayerBlack.setTurn(false);
             }
             System.out.println(currentPlayer.getName() + " plays " + "(" + currentPlayer.getScore() +" points)"  );
             System.out.println("Houses: ");
             printAllHouses(myHouses);//Выводит все дома
             System.out.println("Random number drawn: " + randScoreNum);
             int input = setInput(); //Пользователь вводит инпут
             
             while(!addScoreToHouse(myHouses, currentPlayer, input, randScoreNum)) { //Пока функция возвращает ФОЛС Заново вводить инпут
                 input = setInput();
             }
          }
          System.out.println("\nGAME OVER: ");
          if(PlayerWhite.getScore() > PlayerBlack.getScore()) { //Если очки белого игрока больше то он победил
              System.out.println("WHITE WINS");
          } else if (PlayerWhite.getScore() < PlayerBlack.getScore()) {//Если очки черного игрока больше то он победил
              System.out.println("BLACK WINS");
          } else {//Если одинаковые то ничья
              System.out.println("SPORE");
          }
          
          
   }
   
    public static int setInput() { //Создает и сканирует инпут
        Scanner scanner = new Scanner(System.in);
        System.out.println("To which House do you wish to place the number?");
        int input = scanner.nextInt();
        while(input < 1 || input > 4) { // Если инпут не подходит то сканирует до тех пор пока не подойдет
            System.out.println("\nPls try again: ");
            input = scanner.nextInt();
        }
        return --input; //ВОЗВРАЩАЕТ ИНПУТ - 1!!!
    }
   
   public static boolean isGameContinue(ArrayList<House> Houses) { // Пока хотя бы один дом открыт возвращает ТРУ иначе ФОЛС
       int counter = 0;
       for(int i = 0; i < Houses.size(); i++) {
           if(Houses.get(i).getIsOpened()) {
               return true;
           }
       }
       return false;
   }
   
    public static boolean addScoreToHouse(ArrayList<House> Houses, Player current, int index, int randScore) { // ф-я добавляет очки к ХАУСУ и возвращает ФОЛС в случае ошибки пользователя
        if(!Houses.get(index).getIsOpened()) { //Если ХАУС закрыт то выводит NOPE и возвращает ФОЛС
            System.out.println("NOPE");
            return false;
        }
        if(Houses.get(index).getSum() + randScore < 31) { //Если сумма в доме + рандомные очки меньше 31 то плюсует и возвращает ТРУ
            Houses.get(index).setSum(Houses.get(index).getSum() + randScore);
            Houses.get(index).getNumber().add(randScore);
            return true;
        }
        if (Houses.get(index).getSum() + randScore == 31) {// Если сумма в домк + рандомные очки == 31 то анулирует сумму и чистит массив. Выводит поздравления и возвращает ТРУ
            current.setScore(current.getScore() + 50);
            Houses.get(index).getNumber().clear();
            Houses.get(index).setSum(0);
            System.out.println("*** " + Houses.get(index).getName() + " completes a sum of 31!");
            System.out.println("*** " + current.getName() + " player gains 50 points!");
            return true;
        }
        for(int i = 0; i < Houses.size(); i++) { //Если все предыдущие ифы не сработали то прогоняет массив ХАУСАВ
            if(Houses.get(i).getSum() + randScore < 31) {
                System.out.println("Think..."); // Если в КАЖДОМ ХАУСЕ сумма не будет меньше 31 то выводит ДУМАЙ и возвращает ФОЛС
                return false;
            }
        }
        Houses.get(index).SetOpened(false); // Если ничего не прошло закрывает ХАУС
        return true;
    } 
   
    public static void printAllHouses(ArrayList<House> houses) { // распечатать все 4  дома в виде , который нам нужен 
      for(int i = 0;i<houses.size();i++) {
          if(!houses.get(i).getIsOpened()){ // если закрыт то вывести закрыт 
              System.out.print(houses.get(i).getName() + ": CLOSED!\n");
              continue;
          }
               houses.get(i).printHouse();// если открыт то вывести данные  
        }
  }
   
   public static int randomNumber () { //рандомизирует и возвращает интовое число

    int max = 15; 
    int min = 1; 
       int range = max - min + 1; 
    int random = (int)(Math.random() * range) + min; 
    return random;

  }

}

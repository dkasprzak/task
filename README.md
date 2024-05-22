1. Do usuwania na leży użyć nagłówka [HttpDelete("delete/{id}")]
2. W celu zwiększeznia czytelności i zapewneinia walidaccji scieżki użyj atrybutu [FromRoute] przed parametrem metody public void Delete([FromRoute] unit id){}
3. W przypadku logiki usuwania
 <br>   a) utwórz interfejs np. IUserService gdzie należy utworyć definicję metody do usuwania i klasę UserServcie, gdzie zaiplementujesz metode zdefiniowaną w interfejsie. Do serwisu wstrzyknij DbContext a do metody przensieś logikę związaną z usuwaniem usera. Dobrą opcją będzie też utworzenie prywatnej metody sprawdzajacej czy użytkownik istnieje np. private User GetUserById(uint id){}. Obstawiam, że ta metoda sprzyda się w paru metodach  tego serwisu. Pamiętaj, żeby zarejestrować serwis w klasie rozszerzającej IServiceCollection. Następnie wstzryknij interfejs do kontrolera i użyj metodę usuwania.
    
    <br> b) Jeszce można to bardziej wyabstrachować stosujać repository pattern, gdzie podobnie jak w przypadku serwisu utworzymy IUserRepository i UserRepoistory gdzie utworzymy operację związaną z usuwaniem z bazy, do serwisu wstrzykniemy IUserRepository i w metodzie usuwania wykorzytsamy implementacje z IUserRepository. Potem do konrolera wstrzykniesz IUserServcie i użyjesz metody do usuwania.
4. W przypadku Debug.WriteLine użył bym może prędzej Loggera

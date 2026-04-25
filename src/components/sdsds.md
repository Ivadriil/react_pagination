перейти до: пошук пакетів вмісту вхід

Професіонал
Команди
Ціноутворення
Документація
нпм
Пошук пакетів
Пошук
реагувати на сторінки
Піктограма DefinitelyTyped, яка вказує на те, що цей пакет містить оголошення TypeScript, надані окремим пакетом @types/react-paginate
8.3.0  • Громадськість • Опублікованорік тому
реагувати на сторінки
НПМ Стан збірки

Компонент ReactJS для рендерингу пагінації.

Встановивши цей компонент і написавши лише трохи CSS, ви можете отримати ось що: Примітка: Вам слід написати власний CSS, щоб отримати цей інтерфейс користувача. Цей пакет не надає жодного CSS.

Демонстрація пагінації 2

або

Демонстрація пагінації 1

Встановлення
Встановити react-paginateза допомогою npm :

npm install react-paginate --save
Використання
імпортувати  React ,  {  useEffect ,  useState  }  з  'react' ; 
імпортувати  ReactDOM  з  'react-dom' ; 
імпортувати  ReactPaginate  з  'react-paginate' ;

// Приклади елементів для імітації отримання з інших ресурсів. 
const  items  =  [ 1 ,  2 ,  3 ,  4 ,  5 ,  6 ,  7 ,  8 ,  9 ,  10 ,  11 ,  12 ,  13 ,  14 ] ;

функція  Елементи ( { currentItems } )  { 
  return  ( 
    < > 
      { currentItems  && 
        currentItems.map ( ( item ) = > ( <div> <h3> Елемент № { item } </h3> </div> ) ) } < / > ) ; }​​​​​​​  
          
            
          
        
    
  


function  PaginatedItems ( { itemsPerPage } )  { 
  // Тут ми використовуємо зміщення елементів; ми також можемо використовувати зміщення сторінок 
  // відповідно до API або даних, з якими ви працюєте. 
  const  [ itemOffset ,  setItemOffset ]  =  useState ( 0 ) ;

  // Імітація отримання елементів з інших ресурсів. // (Це можуть бути елементи з props; або елементи 
  , завантажені в локальному стані 
  // з кінцевої точки API за допомогою useEffect та useState) 
  const  endOffset  =  itemOffset  +  itemsPerPage ; 
  console.log ( ` Завантаження елементів з $ { itemOffset } до $ { endOffset } ` ) ; const currentItems = items.slice ( itemOffset , endOffset ) ; const pageCount = Math.ceil ( items.length / itemsPerPage ) ;
      
       

  
  // Викликати , коли користувач клацає , щоб запросити іншу сторінку. const handlePageClick  =  (  event ) =  >  { 
    const  newOffset  =  ( event.selected * itemsPerPage ) % items.length ; console.log ( `Користувач запросив номер сторінки $ { event.selected } , який дорівнює зсуву ${ newOffset } ` ) ; setItemOffset ( newOffset ) ; } ;    
    
      
    
    
  

  повернути  ( 
    < > 
      < Елементи  currentItems = { currentItems }  /> 
      < ReactPaginate 
        breakLabel = "..." 
        nextLabel = "наступний >" 
        onPageChange = { handlePageClick } 
        pageRangeDisplayed = { 5 } 
        pageCount = { pageCount } 
        previousLabel = "< попередній" 
        renderOnZeroPageCount = { null } 
      /> 
    </ > 
  ) ; 
}


// Додайте < div id="container"> до вашого HTML , щоб побачити відображення компонента. ReactDOM.render ( < PaginatedItems itemsPerPage = { 4 } /> , document.getElementById ( 'container' ) ) ;
    
  
Перевірте це на CodePen .

Ви також можете прочитати код demo/js/demo.js , щоб швидко зрозуміти, як працювати react-paginateзі списком об'єктів.

Нарешті, є ця демонстрація CodePen з функціями отримання зразків коду (за допомогою GitHub API) та двома синхронізованими віджетами пагінації.

Реквізит
Ім'я	Тип	Опис
pageCount	Number	Обов’язково. Загальна кількість сторінок.
pageRangeDisplayed	Number	Діапазон відображених сторінок.
marginPagesDisplayed	Number	Кількість сторінок для відображення з полями.
previousLabel	Node	Мітка для previousкнопки.
nextLabel	Node	Мітка для nextкнопки.
breakLabel	Node	Мітка для трикрапки.
breakAriaLabels	Shape	Мітки Aria для елементів еліпса (за замовчуванням { forward: 'Jump forward', backward: 'Jump backward' }).
breakClassName	String	Назва класу на тезі liелемента з трьома крапками.
breakLinkClassName	String	Назва класу на тезі aелемента з трьома крапками.
onPageChange	Function	Метод, який викликається під час зміни сторінки. Надає поточний об'єкт сторінки як аргумент.
onClick	Function	Зворотний виклик для будь-якого кліку на компоненті. Надає інформацію про частину, на яку було зроблено клацання (наприклад, isNextдля наступного елемента керування), наступну очікувану сторінку nextSelectedPageтощо. Може повертати значення false, щоб запобігти будь-якій зміні сторінки, або номер для перевизначення сторінки для переходу.
onPageActive	Function	Метод, який викликається при кліці на активній сторінці. Надає об'єкт активної сторінки як аргумент.
initialPage	Number	Початкова сторінка вибрана в неконтрольованому режимі . Не використовувати з forcePageодночасно.
forcePage	Number	Щоб перезаписати вибрану сторінку батьківською властивістю. Використовуйте це, якщо хочете керувати сторінкою зі стану вашої програми.
disableInitialCallback	boolean	Вимкнути onPageChangeзворотний виклик із початковою сторінкою. За замовчуванням:false
containerClassName	String	Назва класу контейнера пагінації.
className	String	Те саме, що containerClassName. Для використання зі стилізованими компонентами та іншими CSS-in-JS.
pageClassName	String	Назва класу в тезі liкожного елемента сторінки.
pageLinkClassName	String	Назва класу в тезі aкожного елемента сторінки.
pageLabelBuilder	Function	Функція для встановлення тексту на посиланнях сторінок. За замовчуванням(page) => page
activeClassName	String	Назва класу для активної сторінки. Вона об'єднана з базовим класом pageClassName.
activeLinkClassName	String	Назва класу для активного тегу a. Вона об'єднана з базовим класом pageLinkClassName.
previousClassName	String	Назва класу на тезі liкнопки previous.
nextClassName	String	Назва класу на тезі liкнопки next.
previousLinkClassName	String	Назва класу на тезі aкнопки previous.
nextLinkClassName	String	Назва класу на тезі aкнопки next.
disabledClassName	String	Назва класу для disabled previousта nextbuttons.
disabledLinkClassName	String	Назва класу aдля тегу disabled previousта nextbuttons.
hrefBuilder	Function	Метод викликається для генерації hrefзначення атрибута тегу aкожного елемента сторінки.
hrefAllControls	Bool	За замовчуванням hrefBuilderдодається hrefлише до активних елементів керування. Встановіть цю властивість trueтак , щоб hrefвони генерувалися на всіх елементах керування ( див. ).
extraAriaContext	String	ЗАСТАРІЛО: Додатковий контекст для додавання до aria-labelатрибута HTML.
ariaLabelBuilder	Function	Метод викликається для генерації aria-labelзначення атрибута для кожного посилання на сторінку
eventListener	String	Подія, яку потрібно прослухати перед зміною вибраної сторінки. Значення за замовчуванням: onClick.
renderOnZeroPageCount	Function	Функція рендерингу, що викликається when pageCountдорівнює нулю. Нехай кнопки «Попередній» / «Наступний» відображаються за замовчуванням ( undefined). Нічого не відображати when nullпередбачено.
prevRel	String	Властивість relтегу aдля елемента керування попередньою сторінкою. Значення за замовчуванням prev. Встановіть значення , nullщоб вимкнути.
nextRel	String	Властивість relтегу aдля елемента керування наступною сторінкою. Значення за замовчуванням next. Встановіть значення , nullщоб вимкнути.
prevPageRel	String	Властивість relтегу aбезпосередньо перед вибраною сторінкою. Значення за замовчуванням prev. Встановіть значення , nullщоб вимкнути.
selectedPageRel	String	Властивість relтегу aдля вибраної сторінки. Значення за замовчуванням canonical. Встановіть значення , nullщоб вимкнути.
nextPageRel	String	Властивість relтегу aодразу після вибраної сторінки. Значення за замовчуванням next. Встановіть значення , nullщоб вимкнути.

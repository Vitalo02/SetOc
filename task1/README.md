# Первое задание по Сетевым Операционным Системам
## Описание работы программы</br></br>
#### Program1</br></br>

Указание длины массива. </br>
printf("Enter length of array: ");</br>
scanf("%d", &length);</br></br>
Выделение памяти для массива. Если память не выделилась, функция malloc вернёт значение NULL. </br>
if ((array = (int * ) malloc(length * sizeof(int))) != NULL)</br></br>
После этого идет вывод количество байтов, которое было выделено.</br>
printf("Allocated %lu bytes\n", length * sizeof(*array)); </br></br>
Если всё прошло без ошибок, программа очистит выделенную память.</br>
if (array != NULL)</br>
{</br>
free(array);</br>
}</br></br>
#### Program2</br></br>
Выделение памяти для массива элементов типа char.</br>
char * c = (char * ) calloc(100, sizeof(char));</br></br>
 Затем приложение открывает файл foo.txt для чтения и необходимости создания.</br>
int fd = open("foo.txt", O_RDONLY | O_CREAT);</br></br>
После этого происходит вывод значения дескриптора файла</br> 
printf("fd = %d/n", fd);.</br> </br>
Приложение прочтёт из файла 10 байт и запишет полученное количество информации в переменную sz .</br>
sz = read(fd, c, 10);</br></br>
Программа запишет в конец массива терминальный ноль c[sz] = '\0'; и закроет файл</br>
if (close(fd) < 0)</br>
{</br>
perror("close file error:");</br>
exit(1);</br>
}</br></br>
#### Program3</br></br>
Сначала программа вызывает функцию fork(), которая создаёт дочерний процесс </br>
int pid = fork();</br></br>
Затем приложение выведет PID процессы в котором находится.</br>
printf("my pid = %i, returned pid = %i\n", getpid(), pid);</br>
printf("my pid = %i, returned pid = %i\n", getpid(), pid);</br></br>

#### Program4</br></br>
В самом начале программа получает сигнал от пользователя и обрабатывает его.</br>
Затем задаётся глобальная переменная-счётчик counter. </br>
int counter = 0;</br></br>
Также в программе присутствуют две обрабатывающие функции - handler1.</br>
void handler1(int sig)</br>
{</br>
  counter++;</br>
  printf("counter = %d\n", counter);</br>
  /* Flushes the printed string to stdout */</br>
  fflush(stdout);</br>
  kill(pid, SIGUSR1);</br>
}</br></br>
И функция handler2 </br>
void handler2(int sig)</br>
{</br>
  counter += 3;</br>
  printf("counter = %d\n", counter);</br>
  exit(0);</br>
}</br>
Обработка: Программа привязывает первую функцию обработки к текущему процессу.</br>
Далее если процесс окажется дочерним, сигнал будет обрабатывать функция handler2.</br></br>
#### Program5</br></br>
Программа создаёт массив файловых дескрипторов.</br>
После этого приложение проверит корректность ввода и выведет сообщение об ошибке если такая есть. </br>
if (argc != 2)</br>
and</br>
if (pipe(pipefd) == -1)</br></br>
Затем программа вызовет fork() для получения PID дочернего процесса. Дальше приложение проверит только что полученный PID. У дочернего элемента этот идентификатор равен нулю. Далее родительский процесс пишет что-либо.</br>
    close(pipefd[0]);</br>
    write(pipefd[1], argv[1], strlen(argv[1]));</br>
    close(pipefd[1]);</br>
    wait(NULL); </br>
    exit(EXIT_SUCCESS);</br></br>
А дочерний cчитает данные.</br>
if (cpid == 0) </br>
{</br>
    close(pipefd[1]); </br>
    while (read(pipefd[0], & buf, 1) > 0)</br>
      write(STDOUT_FILENO, & buf, 1);</br>
    write(STDOUT_FILENO, "\n", 1);</br>
    close(pipefd[0]);</br>
    _exit(EXIT_SUCCESS);</br></br>
Таким образом реализуется общение между процессами с помощью общего канала.</br></br>

Сначала программа создаёт дескриптор и канал с правами доступа для всех.</br>
int fd; </br>
  int len;</br>
  char buf[BUFSIZE];</br>
    if (mkfifo(NAMEDPIPE_NAME, 0777))</br>
 { </br>
    perror("mkfifo");</br>
    return 1;</br>
  }</br>
</br></br>
После этого запускается бесконечный цикл, в котором приложение прослушивает его.</br>
do {</br>
    memset(buf, '\0', BUFSIZE);</br>
    if ((len = read(fd, buf, BUFSIZE - 1)) <= 0) </br>
    {</br>
      perror("read error");</br>
      close(fd);</br>
      remove(NAMEDPIPE_NAME);</br>
      return 0;</br>
    }</br>
    printf("Incomming message (%d): %s\n", len, buf);</br>
  } while (1);</br></br>
Если программа получила сообщение. </br>
if ((len = read(fd, buf, BUFSIZE - 1)) <= 0)</br>
Производится вывод количество символов (учитывая нуль терминала) и сам текст.</br></br>
## Инструкцию по установке и использованию программы
Каждую программу можно скомпилировать с помощью `gcc <Program_Name.c>`. В директории создастся исполняемый файл `a.out`. Который можно запустить с помощью `./a.out`. </br>
Можно запустить сам Makefile. Запускается как - `make all`. </br>
После этого в папке каждой программы будет создан исполняемый файл с ней (Extension`.out`). </br>
Также можно использовать `make LecN` если не нужны все лекции. Или же `make ProgramN` если нужна определенная программа.</br></br>

Платформы где может работать программа:
+ Ubuntu/Linux - +;
+ Windows - +;
+ OS X - -.

*Расшифровка</br>
Extension - расширение программы</br>
LecN – Номер лекции</br>
ProgramN – Номер программы

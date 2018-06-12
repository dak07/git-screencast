00:06 Поздравляю! Вы поставили git. Теперь мы поговорим о его конфигурации. В этой секции у меня будет несколько выпусков.

00:12 Первый - обязательный, содержит самую базу. Без того, что дальше, в принципе, можно жить, но, конечно, рекомендую посмотреть их все.

00:20 Команда git обычно выглядит так: git и сделай что-то. Например сейчас я нахожусь в директории project в этой директории пока нет файлов. git init создаст там так называемый git репозиторий

00:32 То есть директорию .git которая содержит базу данных и некоторые настройки для git. Это - служебная директория, она находится всегда в корне проекта. 

00:42 Как вы заметили мое командное приветствие немножко изменилось. Это потому, что я, как и говорил в предыдущих выпусках, использую специальный скрипт, который добавляет в командное приветствие информацию о git.

00:52 В данном случае он сообщает, что я нахожусь на ветке master.
Но сейчас это не важно, о ветках мы поговорим потом. 

00:57 Перед тем как добавлять в git данные, давайте поставим основные настройки конфигурации, при помощи команды git config.
И первая настройка, которую я поставлю будет user.name. Она очень важна, потому, что когда мы записываем что-то в git, то git сохраняет кто и когда это сделал.

01:13 Соответственно при командной работе отлично видно, кто автор каких изменений. Без этой информации многие команды гит просто откажутся работать. Так что пишу свое имя, меня зовут "Ilya Kantor" и, также необходимо добавить email.

01:27 Теперь, если мы посмотрим в директории .git есть такой файлик, называется config. Команда cat выводит содержимое файла. и здесь находятся некоторые базовые настройки по-умолчанию, они тут были ранее. А ниже как раз то, что мы добавили. 

01:43 Как видите, формат конфига достаточно простой. Это секция, и под ней значение. То есть user.name переходит в такое-вот свойство name

01:52 В более сложных конфигах возможны подсекции, которые выглядят вот так. То есть дополнительный уровень вложенности обозначается внутри квадратных скобок. То есть вот эти две команды [git config diff.png.textconv "identity -format '%wx%h %b\n'"] [git config diff.png.cachetextconv true] пишут вот сюда [[diff "png"]]

02:04 Прямо сейчас нам это не нужно, но в дальнейшем такие параметры мы тоже будем использовать

02:10 Теперь рассмотрим уровни конфигурации. На одном компьютере современный операционные системы позволяют зарегистрировать несколько пользователей. И у каждого пользователя в разных директориях могут находиться различные проекты.

02:23 git позволяет ставить настройки как общесистемные, так и на уровне конкретного пользователя, так называемые глобальные, и, конечно, на уровне проекта, так называемые локальные, которые мы как раз только что использовали.

02:37 Как мы видели они записываются в директорию .git в файл config. Однако, на практике, как мы с вами очень скоро увидим, большинство настроек находится на глобальном уровне, который относится ко всем проектам пользователя. Это очень удобно, новые проекты сразу их подхватывают.

02:53 Для того, чтобы поставить глобальную настройку используется флаг --global. И такие настройки живут в домашней директории в файле .gitconfig Под Windows это выглядит примерно так [C:\Users\<USERNAME>\.gitconfig] Если вы, по какой-то причине, хотите изменить это местоположение, например, хранить глобальный конфиг на внешнем диске или в специальной директории, выделенной под конфигурацию, то это также возможно.

03:17 Для этого git поддерживает подход предложенный в стандарте XDG. Если вы впервые об этом слышите, ничего страшного, все очень просто. Этот стандарт описывает пути.

03:27 Где должны храниться пользовательские конфигурационные файлы, ползовательские данные и так далее. Он совсем небольшой, буквально пара страниц и вот я прокрутил к переменной, которая нам нужна [XDG_CONFIG_HOME]

03:38 Для хранения пользовательских файлов конфигурации по этому стандарту, должна использоваться директория, путь к которой хранится в переменной окружения XDG_CONFIG_HOME. А если этой переменной нет, то в домашней директории [$HOME\.config]

03:52 Ну а конкретно в случае с git это означает, что если такая переменная окружения существует, то git также использует в качестве глобального файла конфигурации, который находится здесь 
[XDG_CONFIG_HOME/git/config], по такому пути.  Или, если этой переменной нет, то вот здесь [~/config/git/config] 

04:06 При этом, в итоге получается, что у нас могут быть одновременно два глобальных конфиг файла. Однако, на практике, это не удобно, потому, что git хоть и будет читать данные из обоих, но писать команда git config будет только в один.

04:19 Поэтому, если вы хотите использовать такое альтернативное местоположение, то если в домашней директории, уже есть .git/config, то надо его переместить туда. А если нет, то создать пустой файл по этому пути, чтобы гит в дальнейшем использовал именно его.

04:34 Забегая вперед замечу, что в гит также есть дополнительные конфиг файлы, а именно, конфигурация для аттрибутов и для путей, которые надо игнорировать. Мы рассмотрим их в будущих выпусках. Так вот для них тоже работает $XDG_CONFIG_HOME. То есть эта переменная позволяет все глобальные конфигурационные файлы гит положить в выбранную нами директории.

04:53 Последний уровень конфигурации - это системный. То есть параметры, которые в отличие от глобал, не для какого-то пользователя, а вообще на всю систему. Под юникс системами они хранятся в /etc/gitconfig а под windows почти также, но внутри установочной директории гит [C:\Program Files\Git\etc\gitconfig]. Ну и последнее: если вы под windows,
то к этому списку добавляется еще один файл, который по-умолчанию находится вот здесь [C:\ProgramData\Git\config]

05:15 Он создается инсталлятором и содержит настройки, которые были выбраны при установке гит. 

05:19 Итак, у нас три основных уровня и когда гит хочет узнать значение какого-то параметра, то он сначала ищет его локально, то есть в параметрах текущего проекта.
Если там нет - смотрит глобально и, наконец, если и там нет, тогда уже идет в системные.

05:34 Возвращаясь к нашей конкретной конфигурации, имя пользователя, как и его емейл, лучше сделать глобальным, чтобы они автоматически применялись ко всем проектам текущего пользователя. Теперь, если захочу посмотреть значения параметров конфигурации git config --list

05:51 Видите, тут так забавно получилось, что user.name и user.email - дублируются. Это потому, что по-умолчанию --list выводит параметры из всех конфигов. Если я хочу только глобальные значения я могу добавить параметры --global

06:04 Или проще, посмотреть сам файл gitconfig в домашней директории. Давайте я уберу лишние локальные параметры командой git config --unset user.name и git config --unset user.email.

06:18 Или можно было использовать git config --remove-section, чтобы удалить всю секцию user. Ну ка, ну вот, теперь дублирования нет. 

06:27 Здесь для работы с конфигом я использовал специализированную команду. Однако, в реальной жизни зачастую хочется поставить много параметров и сделать это быстро. Поэтому бывает удобно открыть файл конфигурации в редакторе и поменять его напрямую.

06:39 Где находятся файлы для разных уровней конфигурации мы уже видели. В следующем выпуске мы рассмотрим настройку редактора для гит и как раз заодно это сделаем.

06:48 Итак, мы рассмотрели основные опции команды config. На самом деле их гораздо больше. Если хочется посмотреть все, то можно добавить к команде ключ "-h". Этот ключ работает не только с конфигом, но и со многими другими гит командами. Он выводит, видите, все опции и короткое описание. Очень удобно, когда вы уже более-менее знаете опции и хотите быстро вспомнить нужную.

07:10 Более подробную информацию о git config, как и о других командах гит можно получить при помощи "git help" а дальше - команда, которая интересует. Например config. И здесь можно найти как опции самой команды config так и всевозможные настройки конфигурации.

07:27 У гит их очень-очень много. И, пара слов по листалке по-умолчанию. То есть программе, которую использует гит, чтобы вот так вот, посмтранично выводить информацию в терминале. Она называется less. Иногда она бывает некорректно настроена, не переводит строки, запускается даже, когда не надо, то есть когда вывод меньше, чем на одну страницу. В этом случае команду для ее запуска можно сконфигурировать при помощи такого вот параметра: 
[git config --global core.pager 'less -RFX'] его значением можно указать произвольную программу в качестве листалки, которая будет запускать гит. Есть другие, кроме less, но обычно less всем подходит.

08:02 Посмотрите, пожалуйста, на важную особенность less, в левом нижнем углу, там где двоеточие, можно набирать команды. Их у less довольно много, но для комфортного использования необходимо знать хотя бы две. 

08:13 "/" - поиск по регулярному выражению. Скажем, найду строки про editor: [/editor]. Дальше - "n" - поиск вперед, а "shift+n" - поиск назад. Таким образом мы можем быстро найти интересующую нас информацию. И, когда мы все прочитали, то "q" - это выход из листалки.




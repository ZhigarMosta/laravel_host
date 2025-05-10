## Подключение к машине

Проваливаемся в машину `ssh <имя_пользователя>@<удаленный_хост>` для одарённых (простите), имя root, потом собака @, дальше циферки с точкой

## Настройка архитектуры на машине

Cоздаём папку проекта 

```sh
mkdir project
```

Проваливаемся в папку проекта 

```sh
cd project
```

## Подготовка к клонированию проекта на удалённый хост

Из проекта, удаляем папки: `vendor`, `node_modules`, `db_data` последнего может не быть

## Клонированию проекта на удалённый хост

Для этого нужно воспользоваться терминалом, который не подключён к удалённому хосту

Этой командой 

```sh
scp -r . <имя_пользователя>@<удаленный_хост>:/root/project`
```

 клонируется проект в ранее созданую папку `project


Вводим пароль и ждём, пока всё склонируется

## Запуст докера

```sh
./run.sh
```
Командой запускаем docker на удалённомом хосте

## Проверочка хоста

Как только всё запустилось в поисковоую строку вводим 

```sh
http://<удаленный_хост>:9000
```

## Небольшая шпаргалка

```sh 
    public function users():BelongsTo{
        return $this->belongsTo(User::class, 'user_id');
    }
```

```sh 
    public function index(){
        $requests = ModelsRequest::with(['users', 'cars'])->get();
        return view("admin.index",compact("requests"));
    }
```
```sh 
    const ADMIN_ROLE = "admin";

    public function isAdmin(){
        return $this->role === self::ADMIN_ROLE;
    }
```
```sh 
        if(Auth::check()){
            if(auth()->user()->isAdmin() === true){
                return $next($request);
            }
        }
        return redirect('login')->with('error', "Авторизуйтесь под админом"); 
```
```sh 
Route::middleware((Admin::class))->group(function () {
});
```

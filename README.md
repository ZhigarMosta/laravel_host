seeders

создаём его и вписываем его в Dockerfile после строчки  `&& php artisan migrate \` 
строчка должна отличаться только именем `&& php artisan db:seed --class=DatabaseSeeder \`

Проваливаемся в машину `ssh <имя_пользователя>@<удаленный_хост>`

Cоздаём папку проекта 

```sh
mkdir project
```

```sh
cd project
```

Из проекта, удаляем папки: `vendor`, `node_modules`, `db_data` последнего может не быть

 Клонирование проекта на удалённый хост

```sh
scp -r . <имя_пользователя>@<удаленный_хост>:/root/project`
```

в другом терминале запускаем докер

```sh
./run.sh
```
если выдало ошибук `Permission denaided`

```sh
chmod 755 ./run.sh
```

затем пробуем

```sh
./run.sh
```

Как только всё запустилось в поисковоую строку вводим 

```sh
http://<удаленный_хост>:9000
```

## Небольшая шпаргалка

```php
        $cars = DB::table('cars')
        ->join('tests', 'cars.id_test', '=', 'tests.id')
        ->where('cars.name', '=', DB::raw('tests.test'))
        ->where('cars.id', '=', 1)
        ->select('cars.*')
        ->get();
```

```sh 
    public function users():BelongsTo{
        return $this->belongsTo(User::class, 'user_id');
    }
```

```sh
public function cars():HasMany{
        return $this->hasMany(Car::class);
    }
```

```sh 
    public function index(){
        $requests = ModelsRequest::with(['users', 'cars'])->get();
        return view("admin.index",compact("requests"));
    }
```

# reqon_Testes
Repositório para fazer testes antes de implementar no projeto oficial

Arquivos mais importantes

**Migration**

        Schema::create('users', function (Blueprint $table) {
            $table->bigIncrements('id');
            $table->string('name');
            $table->date('birth-date');
            $table->string('cpf',11)->unique();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });

**UserFactory**

    use App\User;
    use Faker\Generator as Faker;

    $factory->define(User::class, function (Faker $faker) {
        return [ 
            'name' => $faker->name,
            'birth-date' => $faker->date(),
            'cpf' => $faker->unique()->numerify('###########'),
            'password' => $faker->lexify('????')
        ];
    });

**Comando para popular**
      
    php artisan tinker
    factory('App\Aluno',10)->create()

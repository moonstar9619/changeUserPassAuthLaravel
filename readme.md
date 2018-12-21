<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## How to change email to phone number

It's a piece of cake! 
- First of all you need to define Password instead of Email so put this method in Controllers/Auth/LoginController.php
    ```
    public function username()
         {
             return 'phone';
         }
    ```
- Then you can put your validation after that
```
    protected function validateLogin(Request $request)
    {
        $request->validate([
            $this->username() => 'required|numeric|regex:/(09)[0-9]{9}/',
            'password' => 'required|string',
        ]);
    }
```    
- At the end in views\auth\login.blade.php chang the field of email to phone input:
```
<div class="form-group row">
    <label for="phone" class="col-sm-4 col-form-label text-md-right">Phone Number</label>
    <div class="col-md-6">
      <input id="phone" type="text" class="form-control{{ $errors->has('phone') ? ' is-invalid' : '' }}" name="phone" value="{{ old('phone') }}" required autofocus>
      @if ($errors->has('phone'))
         <span class="invalid-feedback" role="alert">
            <strong>{{ $errors->first('phone') }}</strong>
         </span>
      @endif
    </div>
</div>  
```  


## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).


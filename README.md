# laravel-short-tips

## Tip - Attempt to read property
```Error: Attempt to read property “name” on null```

 - In view {{ $comment->user->name ?? ‘-‘}}

- Laravel helper ```{{  optional($comment->user)->name )}}```
 - PHP null safe operator ```{{ $comment->user?->name }}```
- In Model for our Comment
  
``` public function users():BelongsTo
{
 return  $this->belongsTo(User::class)
       ->withDefault();
// OR
   ->withDefault([
’name’ => ’None'
])
}
```

## Tip : How to pass dynamic value of options in view from controller
-  Instead of
  ```
   $categories = Category::all();
   return view('products', compact('categories'));

//Blade file
@foreach($categories as $category)
<option value="{{ $category->id}}">{{ $category->name }}</option>
@endforeach
```

Pass categories in controller as : 
```
 $categories = Category::pluck('id','name');
 return view('products', compact('categories'));

// Blade file
@foreach($categories as $id=> $name)
<option value="{{ $id}}">{{ $name }}</option>
@endforeach
```
## Getting age/time diff in years
```
        $date_of_birth = Lead::find(1)->date_of_birth;
        return $date_of_birth->diff(now())->y;
```

# laravel-short-tips

## 1. Tips
```Error: Attempt to read property “name” on null```

 - In view {{ $comment->user->name ?? ‘-‘}}

- Laravel helper {{  optional($comment->user)->name )}}
 - PHP null safe operator {{ $comment->user?->name }}
- In Model for our Comment
  
``` public function users():BelongsTo
{
 return  $this->belongsTo(User::class)
       ->withDefault();
// OR
   ->withDefault([
’name’ => ’None'
])
}```

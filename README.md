# Postgrest Dart

Dart client for [PostgREST](https://postgrest.org). The goal of this library is to make an "ORM-like" restful interface.

[![pub package](https://img.shields.io/pub/v/postgrest.svg)](https://pub.dev/packages/postgrest)
[![pub test](https://github.com/supabase/postgrest-dart/workflows/Test/badge.svg)](https://github.com/supabase/postgrest-dart/actions?query=workflow%3ATest)

Pre-release verion! This repo is still under heavy development and the documentation is evolving. You're welcome to try it, but expect some breaking changes.

## Using

The usage should be the same as postgrest-js except:

- You need to call `execute()` to finish your query chain.
- `is_` and `in_` filter methods are prefixed with `_` sign to avoid collisions with reserved keywords.

You can find detail documentation from [here](https://supabase.io/docs/about).

#### Reading your data

```dart
import 'package:postgrest/postgrest.dart';

var url = 'https://example.com/postgrest/endpoint';
var client = PostgrestClient(url);
var response = await client.from('users').select().execute();
```

#### Insert records

```dart
import 'package:postgrest/postgrest.dart';

var url = 'https://example.com/postgrest/endpoint';
var client = PostgrestClient(url);
var response = await client.from('users')
      .insert([
        { 'username': 'supabot', 'status': 'ONLINE'}
      ])
      .execute();
```

#### Update a record

```dart
import 'package:postgrest/postgrest.dart';

var url = 'https://example.com/postgrest/endpoint';
var client = PostgrestClient(url);
var response = await client.from('users')
      .update({ 'status': 'OFFLINE' })
      .eq('username', 'dragarcia')
      .execute();
```

#### Delete records

```dart
import 'package:postgrest/postgrest.dart';

var url = 'https://example.com/postgrest/endpoint';
var client = PostgrestClient(url);
var response = await client.from('users')
      .delete()
      .eq('username', 'supabot')
      .execute();
```

## Contributing

- Fork the repo on [GitHub](https://github.com/supabase/postgrest-dart)
- Clone the project to your own machine
- Commit changes to your own branch
- Push your work back up to your fork
- Submit a Pull request so that we can review your changes and merge

## License

This repo is liscenced under MIT.

## Credits

- https://github.com/supabase/postgrest-js - ported from postgrest-js library

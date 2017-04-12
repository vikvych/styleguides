# iOS style guides for Objective-C

### Organization

- All method declarations should be documented.
- Use `#pragma marks` to categorize methods into functional groupings and protocol implementations, following this general structure:
```objc
#pragma mark - Navigation
- (void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender;

#pragma mark - Observing
- (void)setupObserving;
- (void)invalidateObserving;

#pragma mark - Actions
- (IBAction)send:(UIButton *)sender;
```
- Use categories where possible as delegate and datasource declarations.
```objc
@interface MyViewController (UITableViewDelegate)

@end
```

### Declaration

- Don't access an ivar unless you're in -init, -dealloc or a custom accessor.
- Use dot-syntax when invoking idempotent methods, including setters and class methods (like `NSFileManager.defaultManager`).
- Comparisons should be explicit for everything except `BOOL`s.
- `nil` check should be explicit
```objc
if (nil != object)
{
	// Do something
}
```

### Spacing

- There should be space after type name with pointer types and no space after `*` symbol.
```objc
NSString *text = @"Sample";
```
- There should be space with operators. Except unary operators.
```objc
int x = (y + z) % 2;
++x;
```
- Method braces and other braces (`if`/`else`/`switch`/`while` etc.) **must** open and close on the new line.
```objc
if (isValid)
{
	// Do something
}
else
{
	// Do something else
}
```
- There **should** be exactly one blank line between methods to aid in visual clarity and organization.
- `@synthesize` and `@dynamic` **must** each be declared on new lines in the implementation.
- Method declaration:
	- There **should** be a space after the scope (- or + symbol). 
	- There **should** be a space between the method segments.
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image;
```

### Variables

Variables **should** be named descriptively, with the variable’s name clearly communicating what the variable is and pertinent information a programmer needs to use that value properly.

### Blocks

- Blocks should have a space between their return type and name.
- Block definitions should omit their return type when possible.
- Block definitions should omit their arguments if they are `void`.
- Parameters in block types should be named unless the block is initialized immediately.
```objc
void (^aBlock)(void) = ^{
    // do some things
};

id (^otherBlock)(id) = ^ id (id args) {
    // do some things
};
```

### Comments

When they are needed, comments **should** be used to explain why a particular piece of code does something. Any comments that are used **must** be kept up-to-date or deleted.

### Literals

`NSString`, `NSDictionary`, `NSArray`, and `NSNumber` literals **should** be used whenever creating immutable instances of those objects.

```objc
NSArray *array = @[@"one", @"two", @"three"];
NSDictionary *dict = @{@"key" : @"value"};
NSNumber *number = @12;
```

# Documentation Coverage TODO

### concrete_subtype and castable_concrete_subtype
- **Test**: Tests/Castable.versetest
- [ ] Only `castable_subtype` is documented
- `concrete_subtype` (FN 37.00+) and `castable_concrete_subtype` (FN 40.00+) are undocumented
- Below their introduction version they silently downgrade to plain `subtype`

## Moderate Gaps

### Effects on interfaces
- **Test**: Tests/Effects.versetest
- [ ] Interfaces accept `<computes>`, `<reads>`, `<allocates>`, `<writes>`, `<transacts>`
- Interfaces reject `<suspends>` and `<decides>` (same as classes/structs)
- Effect inheritance: subtypes can widen but not narrow effects across interface edges
- Docs cover effects on classes but not explicitly on interfaces

### @deprecated details
- **Test**: Tests/Attributes/deprecated.versetest
- [ ] `@deprecated{Message := "..."}` form with custom messages is undocumented
- `DiscontinuedAtFNVersion` field (warning below cutoff, hard error at/above) is undocumented
- @deprecated on modules is undocumented

### @experimental module propagation
- **Test**: Tests/Attributes/experimental.versetest
- [ ] @experimental on a module propagates to all members transitively
- Does NOT propagate up to enclosing module
- Using/importing an experimental module counts as use of experimental

### Join() for localized messages
- **Test**: Tests/LocalizationJoin.versetest
- [ ] `Join(Items:[]message, Separator:message):message` function is undocumented

## Minor Gaps

### `<abstract>` rejected on interfaces and structs
- **Test**: Tests/Attributes/abstract.versetest
- [ ] Docs imply abstract is for classes but don't explicitly state it's invalid on interfaces/structs (error 3596)

### `<concrete>` rejected on interfaces
- **Test**: Tests/Attributes/concrete.versetest
- [ ] `<concrete>` on interfaces gives error 3596
- Cross-module concrete inheritance from abstract base is now valid (was error 3632)

### Default values waive constructor-accessibility requirement
- **Test**: Tests/Classes/AccessSpecifiers.versetest
- [ ] A protected/private member with a default value doesn't need to be as accessible as the constructor

### Delegating constructors capturing Self
- **Test**: Tests/Classes/Constructor.versetest
- [ ] Delegating constructor calls that reference Self implicitly and explicitly

### Qualified method override with multiple interfaces
- **Test**: Tests/Classes/QualifiedMethodInheritance.versetest
- [ ] Override one of two same-named interface methods; the other retains its default via qualified call

### `<override>` required when redeclaring inherited data members
- **Test**: Tests/InterfaceWithFields.versetest
- [ ] Both interface->interface and class->interface redeclaration require `<override>` (error 3532)

### Mutable fields in parametric interfaces
- **Test**: Tests/ParametricFunctions.versetest
- [ ] var fields in parametric interfaces now valid at FN 40.00+

### JSON serialization format change for optionals
- **Test**: Tests/PersonaJson.versetest
- [ ] Optional types now use `"nullable":true` instead of `any_of` with `BOOLEAN`

### `<localizes>` messages in interfaces
- **Test**: Tests/Localization.versetest
- [ ] Interface fields can now use `<localizes>`

### String interpolation with custom operator+
- **Test**: Tests/StringInterpolationPlus.versetest
- [ ] When ToString returns a non-string type and operator+ is defined, string interpolation calls ToString then operator+

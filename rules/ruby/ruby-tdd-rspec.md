---
name: Test-Driven Development in Ruby
---
## Rules

### Do this
  - Write tests before implementing any production code.
  - Ensure tests fail before writing implementation code.
  - Implement only enough code to make the current test pass.
  - Refactor code after tests pass, maintaining green tests.
  - Use descriptive test names and organize tests logically.

### Dont do this
  - Don’t write implementation code before writing a failing test.
  - Don’t skip writing tests for new features or bug fixes.
  - Don’t use third-party test frameworks other than RSpec unless specified.

## Examples

### Good
```rb
# spec/grid_spec.rb
describe Grid do
  it "initializes with a given size" do
    grid = Grid.new(5, 5)
    expect(grid.cells.size).to eq(5)
  end
end

# grid.rb
class Grid
  attr_reader :cells
  def initialize(rows, cols)
    @cells = Array.new(rows) { Array.new(cols, 0) }
  end
end
```

### Bad
```rb
# grid.rb
class Grid
  def initialize(rows, cols)
    @cells = Array.new(rows) { Array.new(cols, 0) }
  end
end

# spec/grid_spec.rb
# (No test written before implementation)
```

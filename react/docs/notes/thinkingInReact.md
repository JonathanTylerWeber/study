<!-- Overview -->

When building UIs with React:

Break the design into reusable components.

Render a static version first (no interactivity).

Identify the minimal state needed.

Decide where the state lives.

Enable inverse data flow so children can update parent state.

<!-- Step 1: Break the UI into a component hierarchy -->

Draw boxes around logical parts of the UI.

Use the single responsibility principle—each component should do one thing.

Example hierarchy:
FilterableProductTable → SearchBar, ProductTable → ProductCategoryRow, ProductRow.

<!-- Step 2: Build a static version -->

Render UI from props only (no state).

Compose components and pass data down.

No interactivity—just JSX structure.

Build top-down for small projects, bottom-up for large ones.

<!-- Step 3: Find the minimal but complete representation of UI state -->

Only keep in state:

Data that changes over time

Data that cannot be computed from props or other state

In the example:
✅ filterText and inStockOnly are state.
❌ Product list and filtered list are not (derived from props/state).

<!-- Step 4: Identify where your state should live -->

For each state:

List components that use it.

Find their closest common parent.

Store state there and pass it down via props.

Example:
Both SearchBar and ProductTable use filterText and inStockOnly → store them in FilterableProductTable.

<!-- Step 5: Add inverse data flow -->

Pass setter functions from parent to child.

Child calls these in onChange handlers to update parent state.

Example:
SearchBar gets onFilterTextChange and onInStockOnlyChange from FilterableProductTable.

# Editing the diagrams

The five `.dot` files are editable Graphviz diagram sources. Views 01–04 use automatic layout; view 05 uses fixed positions for a sequence diagram.

To reproduce the exports from `lab05/` with Graphviz installed:

```sh
for name in 01-context 02-containers 03-components 04-code; do
  dot -Tsvg "diagrams/source/$name.dot" -o "diagrams/exports/$name.svg"
  dot -Tpdf "diagrams/source/$name.dot" -o "diagrams/exports/$name.pdf"
done
neato -n2 -Tsvg diagrams/source/05-dynamic.dot -o diagrams/exports/05-dynamic.svg
neato -n2 -Tpdf diagrams/source/05-dynamic.dot -o diagrams/exports/05-dynamic.pdf
```

The title, labels, colours and relationships can all be edited in the source. For the dynamic diagram, message numbers and vertical positions determine sequence order.

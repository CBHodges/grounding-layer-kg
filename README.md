# The Grounding Layer: A Concept Graph for Knowledge Graphs in Enterprise AI

A small, checked knowledge graph of the core terms behind grounded AI: knowledge graphs, ontologies, provenance, RAG and where it falls short, and grounded abstention.

Built and maintained by **Craig Hodges**, founder of [GoalC.ai](https://www.goalc.ai/about.html) (ALC, Inc.).

## What is in it

- **26 nodes, 225 facts.** 25 concepts plus one concept scheme.
- **Every concept has** a preferred label, a plain-English definition, and a place in the scheme.
- **Concepts link to each other** with broader, narrower and related links. Two extra link types show when one idea contrasts with another, and when one is implemented by another.

## Files

| File | What it is |
|---|---|
| `graph.jsonld` | The graph, in JSON-LD. |
| `schema.json` | A JSON Schema for the file layout, for tools that check plain JSON. |
| `shapes.ttl` | The rules the graph must follow, written in SHACL (the W3C standard for checking graphs). |
| `validation/results.json` | Machine-readable results of the latest check. |
| `validation/conformance-report.docx` | Plain-language summary of the latest check. |

## Proof it was checked

The graph passes its rules with **zero violations**.

The rules were written separately from the data, so the check is a real test. They require things like:

- Every concept has exactly one label and one definition of at least 20 characters.
- Every link points to a real concept in the graph.
- Nothing is both broader and narrower than the same concept.
- "Contrasts with" links are declared on both sides.
- The four RAG-limitation concepts sit under their parent.

To test the rules, we also broke a copy of the graph on purpose in three ways. The check caught all three.

The graph also passes its JSON Schema (`schema.json`).

### Run the check yourself

```bash
pip install pyshacl
pyshacl -s shapes.ttl -sf turtle -df json-ld graph.jsonld
```

A result of `Conforms: True` means the graph passed.

## Explore it online

- Browse it: https://www.goalc.ai/kg/grounding-layer/
- All public graphs: https://www.goalc.ai/kg/

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). You may share and adapt it for noncommercial use, with credit to Craig Hodges / GoalC.ai. For commercial use, contact craighodges@goalc.ai.

## Cite it

See `CITATION.cff`, or use the "Cite this repository" button on GitHub.

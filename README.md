# 🧠 Ontology SysCRED

[![OWL](https://img.shields.io/badge/OWL-2.0-orange.svg)](https://www.w3.org/OWL/)
[![RDF](https://img.shields.io/badge/RDF-Turtle-blue.svg)](https://www.w3.org/TR/turtle/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Ontologies OWL/RDF pour la vérification de crédibilité informationnelle**

PhD Research - Dominique S. Loyer | UQAM

---

## 📋 Overview

Ce repository contient les ontologies développées pour le système **SysCRED** (System for Credibility Evaluation and Detection). Ces ontologies formalisent les concepts de vérification de crédibilité informationnelle en utilisant les standards du Web Sémantique.

L'ontologie définit les concepts suivants:
- **Source**: Entité produisant de l'information (journaliste, média, site web)
- **Claim**: Affirmation ou déclaration à vérifier
- **Evidence**: Preuve supportant ou réfutant une affirmation
- **CredibilityScore**: Score de crédibilité calculé (0.0 à 1.0)

---

## 🚀 Quick Start

### Utilisation avec Python (RDFLib)

```python
from rdflib import Graph

# Charger l'ontologie
g = Graph()
g.parse("sysCRED_data.ttl", format="turtle")

# Requête SPARQL - Obtenir les scores de crédibilité
results = g.query("""
    PREFIX syscred: <http://example.org/syscred#>
    
    SELECT ?source ?score
    WHERE { 
        ?source syscred:hasCredibilityScore ?score 
    }
    ORDER BY DESC(?score)
""")

for row in results:
    print(f"Source: {row.source}, Score: {row.score}")
```

### Visualisation avec Protégé

1. Télécharger [Protégé](https://protege.stanford.edu/)
2. Ouvrir le fichier `sysCRED_data.ttl`
3. Explorer la hiérarchie des classes et les instances

---

## 📁 Project Structure

```
ontology-syscred/
├── README.md           # Ce fichier
└── sysCRED_data.ttl    # ⭐ Ontologie principale (Turtle/RDF)
```

---

## 🔧 Structure de l'Ontologie

### Classes Principales

| Classe | Description |
|--------|-------------|
| `Source` | Origine de l'information |
| `Claim` | Affirmation à vérifier |
| `Evidence` | Preuve factuelle |
| `VerificationResult` | Résultat de vérification |

### Propriétés

| Propriété | Domaine → Range | Description |
|-----------|-----------------|-------------|
| `hasCredibilityScore` | Source → xsd:decimal | Score 0.0 à 1.0 |
| `supports` | Evidence → Claim | Lien de support |
| `refutes` | Evidence → Claim | Lien de réfutation |
| `publishedBy` | Claim → Source | Auteur de l'affirmation |

---

## 📚 Documentation & Papers

- [Ontology of a Verification System (PDF)](https://github.com/DominiqueLoyer/systemFactChecking/blob/main/03_Docs/Ontology_of_a_verification_system_for_liability_of_the_information_may15_2025.pdf)
- [Modeling and Hybrid System (PDF)](https://github.com/DominiqueLoyer/systemFactChecking/blob/main/03_Docs/Modeling%20and%20Hybrid%20System%20for%20Verification%20of%20sources%20credibility.pdf)

---

## 🏷️ Citation

```bibtex
@software{loyer2025ontology,
  author = {Loyer, Dominique S.},
  title = {SysCRED Ontology: Semantic Web Ontology for Information Credibility},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/DominiqueLoyer/ontology-syscred}
}
```

---

## 📜 License

MIT License - See [LICENSE](LICENSE) for details.

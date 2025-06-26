# File Renaming Plan for PRD2PROD Documentation

## Current → Proposed Naming

| Current File                 | Proposed File                    | Status                    |
| ---------------------------- | -------------------------------- | ------------------------- |
| `prd2prod_guidelines.md`     | `prd2prod.md`                    | Main hub - rename         |
| `prd2prod_prd-guidelines.md` | `prd2prod_guide-prd.md`          | Rename                    |
| `prd2prod_workflow-guide.md` | `prd2prod_guide-workflow.md`     | Rename                    |
| `prd2prod_template-prd.md`   | `prd2prod_template-prd.md`       | Keep (already good)       |
| `prd2prod_example1.md`       | `prd2prod_example-csv-export.md` | Rename (more descriptive) |
| *New*                        | `prd2prod_guide-naming.md`       | Create                    |
| *New*                        | `prd2prod_guide-structure.md`    | Create                    |

## Implementation Steps

### Phase 1: Create New Files with New Names

1. Create `prd2prod_guide-naming.md` (extract from current guidelines)
2. Create `prd2prod_guide-structure.md` (extract from current guidelines)
3. Update cross-references in all files

### Phase 2: Rename Existing Files

1. Rename `prd2prod_prd-guidelines.md` → `prd2prod_guide-prd.md`
2. Rename `prd2prod_workflow-guide.md` → `prd2prod_guide-workflow.md`
3. Rename `prd2prod_example1.md` → `prd2prod_example-csv-export.md`
4. Rename `prd2prod_guidelines.md` → `prd2prod.md` (main hub)

### Phase 3: Update All Cross-References

1. Update all internal links to use new filenames
2. Update any external references to these files
3. Test all links work correctly

## Benefits of New Naming Convention

### Logical Grouping

- **Main document first**: `prd2prod.md` appears at top
- **Guides grouped together**: All `prd2prod_guide-*` files sort together
- **Templates grouped**: Easy to find all templates
- **Examples grouped**: All examples in one section

### Scalability

- Easy to add new guides: `prd2prod_guide-testing.md`
- Easy to add new templates: `prd2prod_template-task.md`
- Easy to add new examples: `prd2prod_example-hotfix.md`
- Easy to add references: `prd2prod_reference-glossary.md`

### Clarity

- Purpose clear from filename
- Hierarchical structure obvious
- Consistent pattern across all files

## Alternative Patterns Considered

### Option A: Numbered Prefixes

```
prd2prod_01-overview.md
prd2prod_02-prd-guide.md
prd2prod_03-workflow.md
```

**Rejected**: Numbers become maintenance burden, don't scale well

### Option B: Category Prefixes

```
prd2prod_overview.md
prd2prod_guide-prd.md
prd2prod_guide-workflow.md
```

**Considered**: Good grouping but less clear hierarchy

### Option C: Underscore Separators (Selected)

```
prd2prod_guidelines.md
prd2prod_guide-prd.md
prd2prod_template-task.md
```

**Selected**: Consistent underscore separation, good grouping, clear hierarchy

## Recommendation

Proceed with the **underscore-separated** naming convention for optimal organization and consistency with existing patterns.

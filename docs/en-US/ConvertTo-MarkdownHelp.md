---
external help file: EditorServicesCommandSuite-help.xml
online version: https://github.com/SeeminglyScience/EditorServicesCommandSuite/docs/en-US/ConvertTo-MarkdownHelp.md
schema: 2.0.0
---

# ConvertTo-MarkdownHelp

## SYNOPSIS

Convert the current function from comment based help to markdown.

## SYNTAX

```powershell
ConvertTo-MarkdownHelp [[-Ast] <FunctionDefinitionAst>]
```

## DESCRIPTION

The ConvertTo-MarkdownHelp function will replace existing CBH (comment based help) with markdown generated by the PlatyPS module.  The CBH will be replaced with a EXTERNALHELP comment, and the new markdown file will be opened in the editor.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------

```powershell
ConvertTo-MarkdownHelp
```

Converts the closest CBH to markdown.

### -------------------------- EXAMPLE 2 --------------------------

```powershell
$ast = Find-Ast { $_.GetType().Name -eq 'FunctionDefinitionAst' -and $_.Name -eq 'Invoke-MyCommand' }
```

ConvertTo-MarkdownHelp -Ast $ast

Converts any CBH in the function "Invoke-MyCommand" to markdown.

## PARAMETERS

### -Ast

Specifies the FunctionDefinitionAst containing the CBH to be replaced. The default value is the closest AST to the current cursor location.

```yaml
Type: FunctionDefinitionAst
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: (Find-Ast -AtCursor | Find-Ast -Ancestor -First { $_ -is [FunctionDefinitionAst] })
Accept pipeline input: False
Accept wildcard characters: False
```

## INPUTS

### None

This function does not accept input from the pipeline.

## OUTPUTS

### None

This function does not output to the pipeline.

## NOTES

Markdown generated from PlatyPS is altered in the following ways to conform to linting rules:

- An extra new line is added between headers and content

- Code blocks are marked as PowerShell code

- Trailing spaces after blank aliases fields are removed

- Examples with the header generated as ### Example are replaced with hyphen syntax.

## RELATED LINKS
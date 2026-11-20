# uefi-uefimcp-lch

Servidor MCP de **Licenciatura em Ciências Humanas (LCH)**, UFABC. Nível: **curso** (primeiro ciclo, interdisciplinar).

## Origem

Derivado de [`uefi-uefimcp`](https://github.com/uefiabece/uefi-uefimcp) por `git clone`
(commit de origem registrado em `config/subject.json`), sem importar materiais acadêmicos.
As ferramentas curriculares seguem o padrão de primeiro ciclo de `uefi-uefimcp-lcne`/`uefi-uefimcp-bct` (`plan_academic_journey` recebe o curso de segundo ciclo pretendido).
A camada compartilhada (PDF, SDK MCP v1, `scripts/check_mcp.py`) vem de `uefi-uefimcp-bct` e `uefi-uefimcp-neuro`.

```text
uefi-uefimcp
  └── uefi-uefimcp-lch
      └── 2º ciclo: Licenciatura em Filosofia, Licenciatura em Geografia, Licenciatura em História
```

## Executar

Requer Python 3.11 ou superior. No diretório deste repositório:

```sh
python -m venv .venv
.venv/Scripts/python -m pip install -e ".[pdf,math]"
.venv/Scripts/python run.py
```

O processo usa transporte **stdio**: deve ser iniciado por um cliente MCP.
Em Linux/macOS, use `.venv/bin/python`.

## Conectar

```sh
claude mcp add --scope user uefi-uefimcp-lch -- "CAMINHO_ABSOLUTO/uefi-uefimcp-lch/.venv/Scripts/python.exe" "CAMINHO_ABSOLUTO/uefi-uefimcp-lch/run.py"
```

Outros clientes: veja `config/mcp.example.json`.

## Ferramentas

17 ferramentas:

- **Conteúdo / ensino / exercícios (template):** `get_syllabus`, `get_bibliography`, `get_past_exams`, `search_content`, `get_notes`, `explain_concept`, `get_topic_outline`, `generate_study_plan`, `get_exercises`, `solve_exercise`, `generate_exercise`, `generate_flashcards`
- **Navegação curricular:** `get_curriculum_structure`, `list_subjects_by_area`, `get_disciplinas_limitadas`, `get_progression_requirements`, `plan_academic_journey`

Prompts: `teach` e `solve`.

## Conteúdo

As pastas de `content/` estão vazias. Sugestões: PPC da LCH em `content/bibliography/` e uma síntese em `content/syllabus/curriculo_lch.md`. Ao adicionar o PPC, preencha os metadados em `config/subject.json`.
Sem materiais, as consultas retornam a ausência de conteúdo.

## Verificar

```sh
.venv/Scripts/python scripts/check_mcp.py
```

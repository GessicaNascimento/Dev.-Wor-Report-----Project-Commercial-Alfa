# Dev.-Wor-Report-----Project-Commercial-Alfa

# Developer Work Report — Project Commercial Alfa
**Author:** Géssica Nascimento, data analyst studant 

**Focus:** Infrastructure Consolidation, Environment Debugging, and Pipeline Synchronization

### 1. Incident Log & Infrastructure Debugging

#### Incident 01: CLI Execution vs. Runtime Environment Separation
* **Symptom / Error Message:** ```bash
    Ruca@MacBook-Air Projeto-Alfa-Ltda % pd. to_datetime
    zsh: command not found: pd.
    ```
* **Root Cause Analysis (RCA):** The developer attempted to execute syntax restricted to the Python standard interpreter environment directly inside the native macOS UNIX terminal system interface (`zsh`). The system shell cannot resolve external library wrappers natively.
* **Engineering Resolution:** Encapsulated the code block into a dedicated `.py` deployment script (`projeto_alfa.py`). Established clean environment boundaries where the POSIX shell serves exclusively to call the Python binary runtime compiler (`python3 script.py`), isolating execution.

#### Incident 02: Transient Memory State Allocation (NameError)
* **Symptom / Error Message:**
    ```bash
    Traceback (most recent call last):
      File "/Users/Ruca/Projeto-Alfa-Ltda/projeto_alfa.py", line 10, in <module>
        vendas_mensais.plot(kind='line', marker='o', color='green', linewidth=2)
    NameError: name 'vendas_mensais' is not defined
    ```
* **Root Cause Analysis (RCA):** The Python memory footprint was cleared between decoupled script executions. The script structure attempted to call the aggregation variable `vendas_mensais` for visualization rendering before executing the allocation matrix logic in the active execution pool.
* **Engineering Resolution:** Migrated the system architecture from isolated code snippets into a unified, single-file operational Data Pipeline. Guaranteed that data loading, transformation, aggregation, and rendering occur sequentially in the volatile RAM space before script termination.

#### Incident 03: Feature Dependency Lifecycle Lock (KeyError)
* **Symptom / Error Message:**
    ```bash
    KeyError: "['valor_simulado', 'receita_simulada'] not in index"
    ```
* **Root Cause Analysis (RCA):** A data export routine was triggered using structural target arrays before executing the Feature Engineering phase that appends those exact calculated attributes into the main DataFrame object.
* **Engineering Resolution:** Enforced strict lifecycle ordering within the engine. Configured the file schema so that the spreadsheet compiler can only slice target variables after the mathematical simulation framework completes vector calculations.

---

### 2. Implemented Workspace Milestone Log

* **Milestone 01 — Directory Allocation:** Configured the local UNIX partition by establishing an isolated workspace hierarchy via terminal control commands:
    ```bash
    cd ~ && mkdir Projeto-Alfa-Ltda && cd Projeto-Alfa-Ltda
    ```
* **Milestone 02 — Downstream Engine Setup:** Resolved Excel generation processing issues by auditing and activating the third-party binary spreadsheet bridge tool directly through the package management interface:
    ```bash
    pip3 install openpyxl
    ```
* **Milestone 03 — Multi-Source Integration Interface:** Designed and tested an advanced relational unification mechanism using an identification index key mapping approach (`pd.merge`), joining structured tables into a single source of truth:
    ```python
    df_completo = pd.merge(df_vendas, df_produtos, on='id_produto')
    df_final = pd.merge(df_completo, df_clientes, on='id_cliente')
    ```

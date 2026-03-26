**Что сделано:**

| Изменение | Файлов |
|-----------|--------|
| Версии `18.0.x` → `19.0.x` | 7 manifest + pyproject.toml |
| `groups_id` → `group_ids` | 6 файлов |
| `self._cr` → `self.env.cr` | 1 файл |
| `odoo.osv.expression` → `odoo.fields.Domain` | 6 файлов |
| `read_group` → `_read_group` (новый API) | 1 файл |
| `_sql_constraints` → `_constraints / models.Constraint` | 3 файла |
| `type="json"` → `type="jsonrpc"` | 1 файл |
| `auto_join=` → `bypass_search_access=` | 5 файлов |
| `toggle_active` → `action_archive/action_unarchive` | 1 файл |

**Ветка:** `19.0-migration` — 3 коммита, все локально.

**Что нужно сделать вручную:**
1. `pip install pre-commit && pre-commit run -a` — форматирование кода (особенно после sed-замен)
2. JS/OWL компоненты — проверить вручную на работающем Odoo 19 (файлы `dms/static/src/js/**/*.esm.js`, `dms_field/static/src/**/*.esm.js`)
3. `dms_security_mixin.py` — `NEGATIVE_TERM_OPERATORS` ещё импортируется из `odoo.osv.expression`; если этот импорт удалён в Odoo 19, нужно определить константу локально

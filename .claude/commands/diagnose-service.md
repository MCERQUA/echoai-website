---
description: Run diagnostics on Cloudflare or Supabase services using MCP tools
allowed-tools: Read, Write
---

# 🔍 Service Diagnostics - $ARGUMENTS

## Determine Service Type
Checking which service to diagnose based on: $ARGUMENTS

<ultrathinking>
The user wants me to diagnose either Cloudflare or Supabase issues.
I must remember:
- NEVER use wrangler CLI - only Cloudflare MCP tools
- I have direct API access via MCP tools
- No permission issues when using MCP
</ultrathinking>

## Available Diagnostic Commands

### For Cloudflare Issues:
**Workers:**
- `worker_list` - List all workers
- `worker_get [name]` - Get worker code
- `worker_put` - Deploy worker (NOT wrangler deploy!)

**KV Storage:**
- `kv_list` - List namespaces
- `kv_get [namespace] [key]` - Read value
- `kv_list [namespace]` - List keys

**R2 Storage:**
- `r2_list_buckets` - List all buckets
- `r2_list_objects [bucket]` - List objects

**D1 Database:**
- `d1_list_databases` - List databases
- `d1_query [db_id] [query]` - Run SQL

**Analytics:**
- `analytics_get [zone_id]` - Get analytics

### For Supabase Issues:
**Project Info:**
- `list_projects` - See all projects
- `get_project [id]` - Project details

**Database:**
- `list_tables [project_id]` - View schema
- `execute_sql [project_id] [query]` - Run queries
- `list_migrations [project_id]` - Check migrations

**Debugging:**
- `get_logs [project_id] [service]` - View logs
  - Services: api, auth, storage, realtime, postgres
- `get_advisors [project_id] [type]` - Get recommendations
  - Types: security, performance

**Edge Functions:**
- `list_edge_functions [project_id]` - List functions
- `deploy_edge_function` - Deploy (NOT via CLI!)

Which service would you like to diagnose?
1. Cloudflare Worker issue
2. Cloudflare KV issue  
3. Cloudflare R2 issue
4. Cloudflare D1 issue
5. Supabase database issue
6. Supabase auth issue
7. Supabase storage issue
8. Supabase edge function issue
# CLAUDE.md - Open Artifact Registry

## Project Overview

The **open-artifact-registry** is a simple tool hosted via GitHub Pages that indexes and searches open-source and DevOps tools and resources. It provides a lightweight alternative to more complex catalog solutions like backstage.io.

## Repository Structure

```
.
├── docs/                    # Static site files (served via GitHub Pages)
│   ├── index.html          # Main HTML page
│   ├── app.js              # Client-side JavaScript logic
│   ├── repos.yaml          # Repository/tool catalog data
│   └── CNAME               # Custom domain configuration
├── .github/                 # GitHub configuration and templates
│   └── ISSUE_TEMPLATE/     # Issue templates
├── Dockerfile              # Container configuration
├── docker-compose.yml      # Local development setup
├── Makefile                # Build automation (up/down targets)
├── .pre-commit-config.yaml # Pre-commit hooks configuration
├── CODE_OWNERS             # Code ownership configuration
├── SECURITY.md             # Security policies
└── README.md               # Project documentation
```

## Technology Stack

- **Frontend**: Vanilla HTML/JavaScript
- **Data Store**: YAML (repos.yaml)
- **Local Development**: Docker + Docker Compose
- **Hosting**: GitHub Pages (static site)

## Key Files

### docs/repos.yaml
The main data file containing all indexed tools and repositories. Each entry follows this structure:

```yaml
- name: Tool Name
  url: https://tool.url/
  description: Brief description of the tool
  tags:
    - tag1
    - tag2
```

### docs/app.js
Client-side JavaScript that handles:
- Loading and parsing repos.yaml
- Search functionality
- Tag filtering
- Dynamic content rendering

### docs/index.html
Main UI interface for browsing and searching the artifact registry.

## Development Workflow

### Running Locally

**Prerequisites:**
- Docker
- docker-compose

**Commands:**
```bash
# Start the local development environment
make up

# Stop and clean up containers
make down
```

The Makefile targets handle:
- `make up`: Brings up containers with forced recreation
- `make down`: Removes containers and images

### Adding New Tools/Repositories

To add a new tool to the registry:

1. Edit `docs/repos.yaml`
2. Add a new entry following the existing format
3. Include relevant tags for discoverability
4. Test locally using `make up`
5. Commit and push changes

### Deployment

Changes to the `docs/` directory are automatically deployed to GitHub Pages when pushed to the main branch.

## Coding Standards

- **YAML**: Follow existing indentation (2 spaces)
- **JavaScript**: Maintain vanilla JS approach (no frameworks)
- **HTML**: Keep structure simple and semantic
- **Tags**: Use lowercase, hyphenated tags for consistency

## Common Tags

Based on existing entries:
- `docker`, `containers`, `microservices`
- `kubernetes`, `k8s`, `aks`
- `ci/cd`
- `aws`, `azure`, `gcp`
- `cloud-security`, `devsecops`
- `terraform`, `iac-orchestrators`
- `tools`, `IDE`
- `logging`, `storage`

## Testing Considerations

- Validate YAML syntax after editing repos.yaml
- Test search functionality with new entries
- Verify tag filtering works correctly
- Check responsive layout on different screen sizes

## Security

- See SECURITY.md for security policies
- Pre-commit hooks configured via .pre-commit-config.yaml
- Code owners defined in CODE_OWNERS

## Future Enhancements (TODO)

From README.md:
- [ ] Move to a prettier site with navigation
- [ ] Share the site with the world

## Working with This Repository

When making changes:

1. **Always test locally first** using Docker Compose
2. **Validate YAML** before committing changes to repos.yaml
3. **Follow the existing data structure** when adding entries
4. **Use descriptive commit messages** that explain what tools/changes were added
5. **Check that tags are consistent** with existing taxonomy

## Notes for Claude Code

- This is a static site project - no backend server required
- All data is stored in YAML and processed client-side
- Focus on maintaining simplicity and avoiding over-engineering
- When adding tools, ensure descriptions are concise but informative
- Tags should help with discoverability - think about how users will search

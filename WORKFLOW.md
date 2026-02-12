# Workflow: From Private POC to Public Release

This document describes the workflow for developing and publishing Kiro Powers.

## Repository Strategy

### Private Repository (Power-Builder)
**Purpose:** Proof of Concept and Internal Development

**Location:** `/Users/david/Documents/Git/Power-Builder`

**Characteristics:**
- Spanish documentation
- Docker-based configuration
- Wrapper scripts for local environment
- Absolute paths
- Team-specific configurations
- Rapid experimentation

**Use for:**
- Testing new power ideas
- Docker-based development
- Internal team use
- POC validation

### Public Repository (kiro-powers-aws-public)
**Purpose:** Public Release and Official Submission

**Location:** `/Users/david/Documents/Git/Power-Builder/public-release`

**Characteristics:**
- English documentation
- Generic configurations (uvx commands)
- No wrapper scripts
- Relative paths
- Sanitized credentials
- Community-ready

**Use for:**
- Public sharing
- Official Kiro repository submission
- Community contributions
- Production use

## Development Workflow

### Phase 1: POC Development (Private Repo)

1. **Create power in private repo**
   ```bash
   cd Power-Builder
   mkdir powers/new-power
   # Develop with Docker, Spanish docs, etc.
   ```

2. **Test locally with Docker**
   - Use wrapper scripts
   - Test with team-specific configurations
   - Iterate quickly

3. **Validate functionality**
   - Ensure all workflows work
   - Document issues and solutions
   - Get team feedback

### Phase 2: Adaptation for Public Release

1. **Copy to public-release directory**
   ```bash
   cd Power-Builder/public-release
   mkdir new-power
   ```

2. **Translate documentation to English**
   - Convert POWER.md to English
   - Keep technical accuracy
   - Maintain all sections

3. **Sanitize mcp.json**
   - Remove absolute paths
   - Replace wrapper scripts with uvx commands
   - Use placeholders for credentials
   - Document configuration in POWER.md

4. **Test generic configuration**
   - Install uv locally (if not using Docker)
   - Test with generic mcp.json
   - Verify all workflows work

5. **Update README**
   - Add new power to list
   - Update installation instructions
   - Add usage examples

### Phase 3: Public Release

1. **Commit to public-release repo**
   ```bash
   cd public-release
   git add .
   git commit -m "Add new-power"
   ```

2. **Push to GitHub**
   ```bash
   git remote add origin https://github.com/YOUR-USERNAME/kiro-powers-aws.git
   git push -u origin main
   ```

3. **Test from GitHub**
   - Install in Kiro from GitHub URL
   - Verify functionality
   - Check documentation

### Phase 4: Official Submission (Optional)

1. **Fork official repository**
   ```
   https://github.com/kirodotdev/powers
   ```

2. **Add your power**
   ```bash
   git clone https://github.com/YOUR-USERNAME/powers.git
   cd powers
   cp -r /path/to/public-release/new-power ./
   git add new-power/
   git commit -m "Add new-power"
   git push origin main
   ```

3. **Create Pull Request**
   - Detailed description
   - Usage examples
   - Testing checklist

## Checklist: Private to Public

### Documentation
- [ ] Translate POWER.md to English
- [ ] Verify all sections are complete
- [ ] Add configuration placeholders section
- [ ] Update examples to be generic
- [ ] Remove team-specific references

### Configuration
- [ ] Replace wrapper scripts with uvx commands
- [ ] Remove absolute paths
- [ ] Use environment variable placeholders
- [ ] Document all placeholders in POWER.md
- [ ] Test generic configuration

### Repository Files
- [ ] Update README.md
- [ ] Verify LICENSE file
- [ ] Check .gitignore
- [ ] Remove private/sensitive information

### Testing
- [ ] Test installation from local directory
- [ ] Test installation from GitHub
- [ ] Verify all workflows work
- [ ] Check MCP server connection
- [ ] Validate documentation accuracy

## File Mapping: Private → Public

### Private Repo Structure
```
Power-Builder/
├── powers/
│   └── aws-well-architected/
│       ├── POWER.md (Spanish, detailed)
│       ├── mcp.json (Docker wrapper)
│       ├── mcp.local.json
│       └── mcp.docker.json
├── docker-mcp-wrapper.sh
└── diagnostico-mcp.sh
```

### Public Repo Structure
```
public-release/
├── aws-well-architected/
│   ├── POWER.md (English, generic)
│   └── mcp.json (uvx command)
├── README.md
├── LICENSE
└── .gitignore
```

## Key Differences

| Aspect | Private Repo | Public Repo |
|--------|-------------|-------------|
| Language | Spanish | English |
| Configuration | Docker wrappers | uvx commands |
| Paths | Absolute | Generic |
| Documentation | Team-specific | Community-ready |
| Credentials | Can be specific | Must be placeholders |
| Testing | Docker-based | Generic installation |

## Maintenance

### Updating a Power

1. **Make changes in private repo first**
   - Test with Docker
   - Validate with team

2. **Port changes to public repo**
   - Translate if needed
   - Adapt configuration
   - Test generic version

3. **Push to GitHub**
   ```bash
   cd public-release
   git add .
   git commit -m "Update power-name: description"
   git push
   ```

4. **Update official repo (if applicable)**
   - Create PR with changes
   - Reference issue if fixing bug

### Adding a New Power

Follow the complete workflow from Phase 1 to Phase 4.

## Tips

- **Keep private repo for experimentation** - Don't worry about polish
- **Public repo should be production-ready** - Test thoroughly
- **Document everything** - Future you will thank you
- **Test both configurations** - Docker and generic
- **Get feedback** - From team and community

## Resources

- [Kiro Powers Documentation](https://kiro.dev/docs/powers)
- [Official Powers Repository](https://github.com/kirodotdev/powers)
- [MCP Documentation](https://modelcontextprotocol.io/)

# Prompt File Locations in Open-SWE

This document provides a comprehensive listing of all prompt files in the Open-SWE codebase, organized by category and purpose.

## Overview

The Open-SWE codebase uses a distributed approach to prompt management, with prompts organized by their functional area and co-located with the components that use them. This structure ensures maintainability and clear separation of concerns.

## Core Prompt Files

### 1. Shared Prompts
**File:** `apps/open-swe/src/graphs/shared/prompts.ts`
- **Purpose:** Contains shared prompts used across multiple graphs
- **Key Content:** GitHub workflows permissions prompt that restricts file operations in `.github/workflows/` directory
- **Usage:** Imported by various graph nodes that need common prompt templates

### 2. Plan Formatting Utilities
**File:** `apps/open-swe/src/utils/plan-prompt.ts`
- **Purpose:** Plan formatting utilities and prompt templates for task plan display
- **Key Content:** `PLAN_PROMPT` template with placeholders for completed tasks, remaining tasks, and current task
- **Usage:** Used by nodes that need to format and display task plans in prompts

### 3. Evaluation Prompts
**File:** `apps/open-swe/evals/prompts.ts`
- **Purpose:** Evaluation-related prompts for testing and assessment
- **Key Content:** Prompts used in evaluation workflows and testing scenarios
- **Usage:** Used by evaluation scripts and testing infrastructure

## Graph-Specific Prompt Files

### Manager Graph

#### Message Classification
**File:** `apps/open-swe/src/graphs/manager/nodes/classify-message/prompts.ts`
- **Purpose:** Message classification and routing prompts for the manager graph
- **Key Content:** 
  - Routing options for different message types (update_programmer, start_planner, etc.)
  - Task plan prompt template for contextual routing decisions
- **Usage:** Used by the classify-message node to determine how to route user messages

### Planner Graph

#### Message Generation
**File:** `apps/open-swe/src/graphs/planner/nodes/generate-message/prompt.ts`
- **Purpose:** Message generation prompts for planner communication
- **Key Content:** Templates for generating user-facing messages from the planner
- **Usage:** Used by the planner's generate-message node to create responses

#### Plan Generation
**File:** `apps/open-swe/src/graphs/planner/nodes/generate-plan/prompt.ts`
- **Purpose:** Plan generation prompts for creating task execution plans
- **Key Content:** Templates and instructions for generating structured task plans
- **Usage:** Used by the planner's generate-plan node to create execution plans

### Programmer Graph

#### Message Generation
**File:** `apps/open-swe/src/graphs/programmer/nodes/generate-message/prompt.ts`
- **Purpose:** Message generation prompts for programmer communication
- **Key Content:** Templates for generating user-facing messages from the programmer
- **Usage:** Used by the programmer's generate-message node to create responses and status updates

### Reviewer Graph

#### Review Action Generation
**File:** `apps/open-swe/src/graphs/reviewer/nodes/generate-review-actions/prompt.ts`
- **Purpose:** Review action generation prompts for code review workflows
- **Key Content:** Templates for generating review actions and feedback
- **Usage:** Used by the reviewer's generate-review-actions node to create review recommendations

## Tool-Specific Prompt Files

### Document Search Tool
**File:** `apps/open-swe/src/tools/search-documents-for/prompt.ts`
- **Purpose:** Document search and information extraction prompts
- **Key Content:** 
  - `DOCUMENT_SEARCH_PROMPT` for specialized document information extraction
  - Instructions for precise, thorough information extraction without hallucination
- **Usage:** Used by the search-documents-for tool to extract relevant information from documents

### MCP Output Formatting
**File:** `apps/open-swe/src/utils/mcp-output/prompt.ts`
- **Purpose:** MCP (Model Context Protocol) output formatting prompts
- **Key Content:** Templates for formatting MCP tool outputs and responses
- **Usage:** Used by MCP-related utilities for consistent output formatting

## Web Interface Prompt Files

### GitHub Installation Prompt
**File:** `apps/web/src/components/github/installation-prompt.tsx`
- **Purpose:** UI component for GitHub app installation prompts
- **Key Content:** React component with default props for installation messaging
- **Usage:** Used in the web interface to prompt users to install the GitHub app

## Prompt File Patterns and Conventions

### Naming Conventions
- **Single prompts:** `prompt.ts` (e.g., in generate-message nodes)
- **Multiple prompts:** `prompts.ts` (e.g., in classify-message node)
- **UI components:** `*-prompt.tsx` (e.g., installation-prompt.tsx)

### Structure Patterns
- Most prompt files export constant string templates
- Some include utility functions for formatting prompts (e.g., `formatPlanPrompt`)
- Prompts often use template-like syntax with placeholders (e.g., `{COMPLETED_TASKS}`, `{TASK_PLAN}`)
- Complex prompts are broken into reusable components and options

### Organization Strategy
- **Co-location:** Prompts are placed near the code that uses them
- **Separation by function:** Each graph and tool has its own prompt files
- **Shared resources:** Common prompts are centralized in `graphs/shared/`
- **Utility separation:** Formatting utilities are in the `utils/` directory

## Usage Guidelines

1. **Consistency:** Follow existing naming conventions when creating new prompt files
2. **Co-location:** Place prompts near their consuming code for maintainability
3. **Reusability:** Use shared prompts for common patterns across graphs
4. **Documentation:** Include clear descriptions of prompt purposes and usage
5. **Template syntax:** Use consistent placeholder syntax for dynamic content

## Total Count

**11 prompt files** across the codebase:
- 3 core prompt files
- 5 graph-specific prompt files
- 2 tool-specific prompt files  
- 1 web interface prompt file

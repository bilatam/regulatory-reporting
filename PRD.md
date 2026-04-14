# Planning Guide

Enterprise regulatory reporting management platform designed to centralize the inventory of cash and liquidity regulatory reports for a financial institution, enabling comprehensive tracking, version control, audit trails, and operational monitoring.

**Experience Qualities**:
1. **Professional & Trustworthy** - The interface must inspire confidence through clear visual hierarchy, precise data presentation, and corporate design language suitable for financial operations.
2. **Efficient & Actionable** - Users should quickly access critical information, download reports, track compliance status, and identify issues without cognitive overhead.
3. **Comprehensive & Auditable** - Every action, version, and change must be traceable, providing complete transparency for regulatory compliance and internal audits.

**Complexity Level**: Complex Application (advanced functionality, likely with multiple views)
This is a multi-module enterprise platform requiring sophisticated data management, role-based access, multiple interconnected views (dashboard, inventory, detail screens, calendar, analytics), version control, audit trails, and complex filtering/search capabilities across 20+ regulatory reports.

## Essential Features

### Dashboard Ejecutivo
- **Functionality**: Executive overview displaying KPIs, compliance metrics, alerts, and upcoming deadlines
- **Purpose**: Enables leadership and supervisors to quickly assess regulatory compliance status and identify risks
- **Trigger**: Default landing page after login, accessible from sidebar
- **Progression**: View KPIs → Identify alerts → Click metric to drill down → Navigate to detailed view
- **Success criteria**: All KPIs update dynamically, charts render correctly, alerts are visible, drill-down navigation works

### Inventario de Reportes
- **Functionality**: Comprehensive data grid with advanced filtering, sorting, search, and export capabilities for all 20 regulatory reports
- **Trigger**: Click "Inventario" in sidebar or drill-down from dashboard metrics
- **Progression**: Load table → Apply filters (regulator/frequency/status/criticality) → Sort columns → Search by name → Select report → Open detail view
- **Success criteria**: Filters work independently and combined, search is instant, table sorts correctly, detail opens on row click

### Detalle del Reporte
- **Functionality**: Full-screen detail view with tabs for summary, history, versions, files, audit log, incidents, calendar, dependencies, and comments
- **Purpose**: Provides complete information about a single report including all metadata, downloadable files, and traceability
- **Trigger**: Click any report row in inventory or dashboard
- **Progression**: Open detail → View summary tab → Switch between tabs → Download files → View version history → Read audit log → Return to inventory
- **Success criteria**: All tabs render with appropriate data, file downloads work, version comparison displays, timeline shows chronological events

### Descarga de Reportes
- **Functionality**: Dedicated section for downloading current and historical versions of reports in multiple formats
- **Purpose**: Streamlines access to report files for analysts and regulators
- **Trigger**: Navigate to "Descargas" from sidebar or click download in report detail
- **Progression**: Select report → Choose version/period → Select format → Download → Track download in audit log
- **Success criteria**: Download simulates file retrieval, tracks user action, supports multiple formats, shows download history

### Exportaciones Programadas
- **Functionality**: Automated export scheduling system allowing users to configure reports to be generated and distributed automatically on specific dates or frequencies
- **Purpose**: Eliminates manual repetitive export tasks, ensures timely report distribution, and provides reliable automated delivery to stakeholders
- **Trigger**: Navigate to "Exportaciones" from sidebar or create schedule from report detail
- **Progression**: Create schedule → Select report → Choose frequency (daily/weekly/monthly/quarterly/custom dates) → Select export formats → Add recipients → Configure options (compression, version inclusion) → Activate → Monitor execution
- **Success criteria**: Schedules persist across sessions, support multiple frequencies including custom dates, execute on time, track execution history, allow pause/resume/delete, show next execution date, support multiple file formats per schedule

### Historial y Trazabilidad
- **Functionality**: Complete timeline of all actions, changes, approvals, and incidents for each report
- **Purpose**: Ensures full audit trail for regulatory compliance and internal controls
- **Trigger**: View "Historial" or "Bitácora" tab in report detail
- **Progression**: Open timeline → View events chronologically → Filter by event type → Expand event details → Export audit log
- **Success criteria**: Timeline displays all events with user/date/action, filterable by type, exportable for audits

### Gestión de Versiones
- **Functionality**: Version control system showing current version, historical versions, change reasons, approval status
- **Purpose**: Track report evolution and enable rollback if needed
- **Trigger**: Click "Versiones" tab in report detail
- **Progression**: View version list → Compare versions → Read change notes → Restore previous version → Log action
- **Success criteria**: Versions display with metadata, comparison highlights differences, restore updates current version

### Calendario Regulatorio
- **Functionality**: Visual calendar showing generation dates, submission deadlines, review periods, and alerts
- **Purpose**: Helps teams plan and meet regulatory deadlines
- **Trigger**: Click "Calendario" in sidebar
- **Progression**: View month/week/list → See upcoming deadlines → Filter by regulator/criticality → Click event → Open report detail
- **Success criteria**: Calendar renders all deadlines, color-coded by urgency, filterable, clickable to detail

### Gestión de Incidencias
- **Functionality**: Issue tracking system for recording and managing report-related incidents
- **Purpose**: Centralizes problem management and corrective actions
- **Trigger**: Click "Incidencias" in sidebar or "Incidencias" tab in report detail
- **Progression**: View open incidents → Create new incident → Assign severity/owner → Add corrective action → Close incident → Track resolution time
- **Success criteria**: Incidents filterable by status/severity, editable, linked to specific reports, tracked in audit log

### Buscador Global
- **Functionality**: Intelligent search across all reports, filtering by name, code, regulator, process, keywords
- **Purpose**: Enables rapid access to specific reports without navigation
- **Trigger**: Click search icon in topbar or use keyboard shortcut
- **Progression**: Open search → Type query → View results → Click result → Navigate to report detail
- **Success criteria**: Search is instant, matches partial queries, highlights results, supports keyboard navigation

### Exportación y Analítica
- **Functionality**: Generate analytics reports on compliance rates, incident trends, download statistics, version changes
- **Purpose**: Provides management insights for operational improvement
- **Trigger**: Click "Analítica" in sidebar
- **Progression**: View metrics dashboard → Select date range → Filter by area/regulator → Export report → Download analytics
- **Success criteria**: Charts render correctly, filters update data, export generates file

## Edge Case Handling

- **No Data Available** - Display empty states with helpful guidance to add reports or check filters
- **Network/Loading Delays** - Show skeleton loaders and loading states during data fetching
- **Invalid Filters** - Clear filters if no results, show "No results found" message with reset option
- **Missing File Downloads** - Display message if file unavailable, log attempt in audit trail
- **Simultaneous Edits** - Show last modified timestamp, warn if data may be stale
- **Version Conflicts** - Prevent restore if newer version exists, require confirmation
- **Date Range Errors** - Validate that end date > start date in filters, show inline error
- **Permission Restrictions** - Hide/disable actions user cannot perform based on role
- **Large Tables** - Implement pagination and virtualization for performance
- **Search No Results** - Suggest alternative queries, show recent searches

## Design Direction

The design should evoke **institutional trust, operational precision, and executive clarity**. It should feel like a sophisticated financial operations platform used by central banks and regulators - serious, data-rich, yet approachable for business users. The aesthetic should balance corporate professionalism with modern digital UX, avoiding both outdated banking interfaces and overly casual consumer apps.

## Color Selection

The palette combines deep institutional blues with alert-appropriate accent colors, creating a professional yet accessible financial environment.

- **Primary Color**: Deep Financial Blue (oklch(0.45 0.12 250)) - Communicates trust, stability, and financial authority used for main actions and brand elements
- **Secondary Colors**: 
  - Cool Slate (oklch(0.55 0.02 240)) for secondary actions and borders
  - Neutral Gray (oklch(0.65 0.01 240)) for muted backgrounds and disabled states
- **Accent Color**: Amber Warning (oklch(0.72 0.15 80)) - Attention for deadlines, pending reviews, and important alerts
- **Status Colors**:
  - Success Green (oklch(0.65 0.15 145)) for approved/compliant
  - Alert Red (oklch(0.60 0.20 25)) for overdue/incidents
  - Info Teal (oklch(0.60 0.10 200)) for informational states
- **Foreground/Background Pairings**:
  - Background (oklch(0.98 0 0)): Foreground (oklch(0.25 0.02 240)) - Ratio 12.1:1 ✓
  - Primary Blue (oklch(0.45 0.12 250)): White text (oklch(1 0 0)) - Ratio 8.2:1 ✓
  - Accent Amber (oklch(0.72 0.15 80)): Dark text (oklch(0.25 0.02 240)) - Ratio 7.8:1 ✓
  - Success Green (oklch(0.65 0.15 145)): White text (oklch(1 0 0)) - Ratio 4.9:1 ✓
  - Alert Red (oklch(0.60 0.20 25)): White text (oklch(1 0 0)) - Ratio 5.1:1 ✓

## Font Selection

Typography should balance professional gravitas with excellent readability for data-heavy interfaces. **IBM Plex Sans** as primary typeface brings technical precision and clarity while maintaining warmth, paired with **JetBrains Mono** for codes and identifiers.

- **Typographic Hierarchy**:
  - H1 (Page Title): IBM Plex Sans SemiBold/32px/tight letter-spacing/-0.02em
  - H2 (Section Header): IBM Plex Sans SemiBold/24px/normal letter-spacing
  - H3 (Card Title): IBM Plex Sans Medium/18px/normal letter-spacing
  - Body (Primary Text): IBM Plex Sans Regular/15px/line-height 1.6
  - Small (Metadata/Labels): IBM Plex Sans Regular/13px/line-height 1.5/color muted
  - Code (IDs/Codes): JetBrains Mono Regular/14px/letter-spacing -0.01em
  - Button Text: IBM Plex Sans Medium/14px/letter-spacing 0.01em

## Animations

Animations should feel precise and purposeful, reinforcing the sense of a well-engineered system. Transitions should be quick (150-250ms) to maintain productivity, with subtle easing that feels mechanical yet refined. Use micro-interactions for status changes, hover states on data rows, smooth tab transitions, and gentle fade-ins for modals. Chart animations should sequence data points with brief delays for visual interest. Avoid bouncy or playful animations - everything should feel controlled and professional.

## Component Selection

- **Components**:
  - Sidebar navigation for main modules with collapsible groups
  - Card components for KPIs with icon, metric, trend indicator
  - Table with sortable headers, row selection, inline actions
  - Tabs for report detail views with underline indicator
  - Badge for status indicators (color-coded by state)
  - Dialog for file upload, incident creation, version comparison
  - Calendar component for regulatory deadline tracking
  - Command palette (cmdk) for global search
  - Dropdown-menu for row actions and bulk operations
  - Tooltip for metadata and explanatory text
  - Progress indicators for compliance metrics
  - Breadcrumb for navigation context
  - Alert banners for system notifications
  - Popover for quick actions and filters
  - Separator for content organization
  
- **Customizations**:
  - Custom timeline component for audit log display (vertical line with event nodes)
  - Custom stat card with comparison data and sparkline charts
  - Custom filter panel with multi-select dropdowns and date range pickers
  - Custom status badge system with predefined variants
  - Custom empty states with contextual illustrations and CTAs
  - Custom data export button with format selection dropdown
  
- **States**:
  - Buttons: Default subtle shadow, hover lifts slightly with stronger shadow, active presses down, disabled fades to 50% opacity
  - Table rows: Hover shows light background, selected adds left border accent, clickable shows pointer cursor
  - Inputs: Default border, focus shows ring with brand color, error shows red border with icon, success shows green check
  - Cards: Subtle border, hover elevates with shadow (for interactive cards)
  - Badges: Solid backgrounds with appropriate text colors per status
  
- **Icon Selection**:
  - ChartBar for dashboard/analytics
  - FolderOpen for inventory
  - CalendarDots for calendar view
  - Clock for scheduled exports
  - Warning for incidents
  - Download for file downloads
  - ClockCounterClockwise for history
  - GitBranch for versions
  - MagnifyingGlass for search
  - Bell for notifications
  - User for profile/roles
  - FileText for reports
  - CheckCircle/XCircle/Clock for statuses
  - Play/Pause for schedule control
  - PaperPlaneTilt for email distribution
  - FileZip for compressed archives
  
- **Spacing**:
  - Container padding: p-6
  - Card padding: p-5
  - Section gaps: gap-6
  - Component gaps: gap-4
  - Tight spacing (labels): gap-1.5
  - Page margins: mx-auto max-w-7xl
  
- **Mobile**:
  - Sidebar collapses to hamburger menu
  - KPI cards stack vertically
  - Tables become scrollable horizontally or switch to card layout
  - Tabs become dropdown selector
  - Filter panel becomes bottom sheet
  - Reduce padding/spacing by 25%
  - Touch targets minimum 44px
  - Sticky headers for tables and detail views

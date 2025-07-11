# Lesson Management System

## Overview

This is a browser-based JavaScript application designed for tutors to manage lessons, students, and payments. The application is built as a single-page application that runs entirely in the browser without requiring any server-side components. All interface elements are in Russian, making it accessible for Russian-speaking tutors.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Single Page Application (SPA)**: The entire application is contained in a single HTML file
- **Tabbed Interface**: Three main sections organized as tabs:
  - Calendar (Календарь) - lesson scheduling and management
  - Students (Ученики) - student information management
  - Payments (Оплаты) - payment tracking and notifications
- **Responsive Design**: Uses Tailwind CSS for responsive layout optimized for desktop and tablet

### Client-Side Only Architecture
- **No Backend**: All functionality runs in the browser
- **Local Storage**: Data persistence handled through browser's localStorage
- **File-Based Import/Export**: JSON and Excel file export/import capabilities

## Key Components

### 1. Calendar Management
- **Library**: FullCalendar.js v6.1.8
- **Features**: 
  - Monthly view with drag-and-drop lesson rescheduling
  - Color-coded lessons by status (green=completed, yellow=scheduled, red=cancelled)
  - Modal-based lesson editing
  - Russian localization

### 2. Student Management
- **Library**: Tabulator.js v5.5.0
- **Features**:
  - Inline editing of student data
  - Student information: name, contact, lesson rate, paid lessons count
  - Add/edit/delete student functionality

### 3. Payment Tracking
- **Automatic Notifications**: Alerts when students have less than 2 paid lessons
- **Payment Recording**: Manual payment entry with lesson count and amount
- **Balance Management**: Tracks remaining paid lessons per student

### 4. Data Export/Import
- **JSON Export/Import**: Full data backup and restore functionality
- **Excel Export**: Uses SheetJS to create Excel files with separate sheets for students, payments, and lessons

## Data Flow

### Data Storage Structure
```javascript
{
  students: [
    {
      id: number,
      name: string,
      contact: string,
      rate: number,
      paidLessons: number
    }
  ],
  lessons: [
    {
      id: string,
      title: string,
      start: datetime,
      studentId: number,
      status: string
    }
  ],
  payments: [
    {
      id: number,
      studentId: number,
      amount: number,
      lessonsCount: number,
      date: datetime
    }
  ]
}
```

### Data Persistence Flow
1. **Local Storage**: All data automatically saved to browser localStorage
2. **JSON Export**: User can download complete data as JSON file
3. **JSON Import**: User can upload JSON file to restore data
4. **Excel Export**: Generate Excel report with formatted data

## External Dependencies

### CDN Libraries
- **Tailwind CSS**: UI framework for responsive design
- **FullCalendar.js v6.1.8**: Calendar component with Russian localization
- **Tabulator.js v5.5.0**: Table component for student data management
- **SheetJS**: Excel file generation and export

### No Server Dependencies
- Application runs entirely in browser
- No API calls or server communication required
- All data processing handled client-side

## Deployment Strategy

### Single File Deployment
- **Architecture**: Everything contained in single `index.html` file
- **Assets**: All CSS and JavaScript embedded inline
- **Dependencies**: Loaded from CDN sources
- **Hosting**: Can be deployed to any static hosting service or run locally

### Browser Compatibility
- **Modern JavaScript**: Uses ES6+ features
- **Browser Requirements**: Modern browsers with JavaScript support
- **No Installation**: Runs directly in browser without additional software

### Development Environment
- **Replit Compatible**: Designed to work in Replit's browser preview
- **No Build Process**: Direct HTML file execution
- **Instant Preview**: Changes reflected immediately in browser

## Technical Implementation Notes

### Code Organization
- **Modular Functions**: Separate functions for calendar, student, and payment logic
- **Event Handling**: Modern JavaScript event listeners
- **Modal Management**: Custom modal system for editing interfaces
- **Tab Management**: JavaScript-based tab switching

### Error Handling
- **Graceful Degradation**: Application continues to work if external CDNs fail
- **Data Validation**: Input validation for all user-entered data
- **LocalStorage Fallback**: Handles cases where localStorage might not be available

### Performance Considerations
- **Client-Side Processing**: All operations handled in browser
- **Memory Management**: Efficient data structures for student and lesson management
- **Responsive Updates**: Real-time updates to all interface components
import { useState, useEffect, useRef } from 'react';
import { Calendar as CalendarIcon, Clock, Download, FileText, Plus, X, Check, Power, ChevronLeft, ChevronRight, Share2 } from 'lucide-react';

type AttendanceRecord = {
  id: string;
  date: string;
  checkIn?: string;
  checkOut?: string;
  status: 'present' | 'leave' | 'holiday';
  leaveReason?: string;
};

// Sri Lankan public holidays (sample data)
const sriLankanHolidays = [
  '2023-01-04', '2023-01-15', '2023-02-04', '2023-03-08', 
  '2023-04-14', '2023-04-15', '2023-05-01', '2023-05-05',
  '2023-05-26', '2023-06-03', '2023-07-09', '2023-08-21',
  '2023-09-28', '2023-10-13', '2023-10-24', '2023-12-25'
];

const CalendarMonth = ({ 
  year, 
  month, 
  records,
  onMonthChange 
}: {
  year: number;
  month: number;
  records: AttendanceRecord[];
  onMonthChange: (newMonth: number, newYear: number) => void;
}) => {
  const daysInMonth = new Date(year, month + 1, 0).getDate();
  const firstDayOfMonth = new Date(year, month, 1).getDay();
  const adjustedFirstDay = firstDayOfMonth === 0 ? 6 : firstDayOfMonth - 1; // Make Monday first day
  
  const monthNames = [
    'January', 'February', 'March', 'April', 'May', 'June',
    'July', 'August', 'September', 'October', 'November', 'December'
  ];

  const prevMonth = () => {
    if (month === 0) {
      onMonthChange(11, year - 1);
    } else {
      onMonthChange(month - 1, year);
    }
  };

  const nextMonth = () => {
    if (month === 11) {
      onMonthChange(0, year + 1);
    } else {
      onMonthChange(month + 1, year);
    }
  };

  const renderCalendarDays = () => {
    const days = [];
    
    // Add empty cells for days before the first day of the month
    for (let i = 0; i < adjustedFirstDay; i++) {
      days.push(<div key={`empty-${i}`} className="h-8 w-8"></div>);
    }

    // Add cells for each day of the month
    for (let day = 1; day <= daysInMonth; day++) {
      const dateStr = `${year}-${String(month + 1).padStart(2, '0')}-${String(day).padStart(2, '0')}`;
      const isHoliday = sriLankanHolidays.includes(dateStr);
      const isSunday = new Date(year, month, day).getDay() === 0;
      const isSaturday = new Date(year, month, day).getDay() === 6;
      
      const record = records.find(r => r.date === dateStr);
      
      let bgColor = 'bg-white';
      let textColor = 'text-gray-900';
      
      if (isSunday) {
        bgColor = 'bg-red-50';
        textColor = 'text-red-600';
      } else if (isSaturday) {
        bgColor = 'bg-gray-50';
        textColor = 'text-gray-600';
      }
      
      if (isHoliday) {
        bgColor = 'bg-yellow-50';
        textColor = 'text-yellow-600';
      }
      
      if (record) {
        if (record.status === 'holiday') {
          bgColor = 'bg-yellow-100';
          textColor = 'text-yellow-700';
        } else if (record.status === 'leave') {
          bgColor = 'bg-blue-100';
          textColor = 'text-blue-700';
        } else if (record.checkIn && record.checkOut) {
          bgColor = 'bg-green-100';
          textColor = 'text-green-700';
        } else if (record.checkIn) {
          bgColor = 'bg-orange-100';
          textColor = 'text-orange-700';
        }
      }

      days.push(
        <div 
          key={day} 
          className={`h-8 w-8 flex items-center justify-center rounded-full ${bgColor} ${textColor} text-sm font-medium`}
        >
          {day}
        </div>
      );
    }

    return days;
  };

  return (
    <div className="bg-white rounded-xl shadow-lg overflow-hidden">
      <div className="flex items-center justify-between p-4 bg-gradient-to-r from-blue-600 to-blue-800 text-white">
        <button onClick={prevMonth} className="p-1 rounded-full hover:bg-blue-700">
          <ChevronLeft className="w-5 h-5" />
        </button>
        <h3 className="text-lg font-bold">
          {monthNames[month]} {year}
        </h3>
        <button onClick={nextMonth} className="p-1 rounded-full hover:bg-blue-700">
          <ChevronRight className="w-5 h-5" />
        </button>
      </div>
      
      <div className="p-4">
        <div className="grid grid-cols-7 gap-1 mb-2">
          {['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'].map(day => (
            <div key={day} className={`text-center text-sm font-medium ${
              day === 'Sun' ? 'text-red-600' : day === 'Sat' ? 'text-gray-600' : 'text-gray-700'
            }`}>
              {day}
            </div>
          ))}
        </div>
        
        <div className="grid grid-cols-7 gap-1">
          {renderCalendarDays()}
        </div>
      </div>
    </div>
  );
};

export default function App() {
  const [records, setRecords] = useState<AttendanceRecord[]>(() => {
    const saved = localStorage.getItem('attendanceRecords');
    return saved ? JSON.parse(saved) : [];
  });
  const [currentDate] = useState(new Date().toISOString().split('T')[0]);
  const [currentTime, setCurrentTime] = useState('');
  const [showLeaveDialog, setShowLeaveDialog] = useState(false);
  const [showHolidayDialog, setShowHolidayDialog] = useState(false);
  const [leaveReason, setLeaveReason] = useState('');
  const [leaveType, setLeaveType] = useState('sick');
  const [currentMonth, setCurrentMonth] = useState(new Date().getMonth());
  const [currentYear, setCurrentYear] = useState(new Date().getFullYear());
  const [showCalendar, setShowCalendar] = useState(false);
  const calendarRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    localStorage.setItem('attendanceRecords', JSON.stringify(records));
  }, [records]);

  useEffect(() => {
    const updateTime = () => {
      const now = new Date();
      setCurrentTime(now.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit', second: '2-digit' }));
    };
    
    updateTime();
    const timer = setInterval(updateTime, 1000);
    return () => clearInterval(timer);
  }, []);

  const handleAttendanceAction = () => {
    const todayRecord = records.find(r => r.date === currentDate);
    const now = new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit', second: '2-digit' });
    
    if (!todayRecord) {
      setRecords([...records, {
        id: Date.now().toString(),
        date: currentDate,
        checkIn: now,
        status: 'present'
      }]);
    } else if (todayRecord.checkIn && !todayRecord.checkOut) {
      const updatedRecords = records.map(record => 
        record.date === currentDate ? { ...record, checkOut: now } : record
      );
      setRecords(updatedRecords);
    }
  };

  const handleLeaveRequest = () => {
    setRecords([...records, {
      id: Date.now().toString(),
      date: currentDate,
      status: 'leave',
      leaveReason: `${leaveType}: ${leaveReason}`
    }]);
    setShowLeaveDialog(false);
    setLeaveReason('');
  };

  const handleHoliday = () => {
    setRecords([...records, {
      id: Date.now().toString(),
      date: currentDate,
      status: 'holiday'
    }]);
    setShowHolidayDialog(false);
  };

  const exportToExcel = () => {
    const csvContent = [
      ['Date', 'Check In', 'Check Out', 'Status', 'Leave Reason'],
      ...records.map(record => [
        record.date,
        record.checkIn || '',
        record.checkOut || '',
        record.status,
        record.leaveReason || ''
      ])
    ].map(e => e.join(',')).join('\n');
    
    const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
    const url = URL.createObjectURL(blob);
    const link = document.createElement('a');
    link.href = url;
    link.setAttribute('download', `attendance-${currentDate}.csv`);
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
  };

  const shareViaWhatsApp = () => {
    const data = records.map(record => (
      `Date: ${record.date}\n` +
      `Check In: ${record.checkIn || '-'}\n` +
      `Check Out: ${record.checkOut || '-'}\n` +
      `Status: ${record.status === 'leave' ? 'On Leave' : record.status === 'holiday' ? 'Public Holiday' : 'Present'}\n` +
      `${record.leaveReason ? `Reason: ${record.leaveReason}\n` : ''}`
    )).join('\n');

    const whatsappUrl = `https://wa.me/?text=${encodeURIComponent(`My Attendance Records:\n\n${data}`)}`;
    window.open(whatsappUrl, '_blank');
  };

  const handleMonthChange = (newMonth: number, newYear: number) => {
    setCurrentMonth(newMonth);
    setCurrentYear(newYear);
  };

  const todayRecord = records.find(r => r.date === currentDate);
  const attendanceButtonText = !todayRecord 
    ? 'Check In' 
    : todayRecord.checkIn && !todayRecord.checkOut 
      ? 'Check Out' 
      : 'Attendance Recorded';

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-50 to-indigo-50 p-4 max-w-md mx-auto">
      {/* Header */}
      <header className="mb-6">
        <h1 className="text-2xl font-bold text-center text-blue-800">Attendance Tracker</h1>
        <div className="flex justify-between items-center mt-2">
          <div className="flex items-center text-sm text-blue-600">
            <CalendarIcon className="w-4 h-4 mr-1" />
            <span>{new Date().toLocaleDateString('en-US', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}</span>
          </div>
          <div className="flex items-center text-sm text-blue-600">
            <Clock className="w-4 h-4 mr-1" />
            <span className="tabular-nums">{currentTime}</span>
          </div>
        </div>
      </header>

      {/* Calendar Toggle */}
      <div className="mb-4 flex justify-center">
        <button 
          onClick={() => setShowCalendar(!showCalendar)}
          className="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
        >
          {showCalendar ? 'Hide Calendar' : 'Show Calendar'}
        </button>
      </div>

      {/* Calendar View */}
      {showCalendar && (
        <div className="mb-6" ref={calendarRef}>
          <CalendarMonth 
            year={currentYear} 
            month={currentMonth} 
            records={records}
            onMonthChange={handleMonthChange}
          />
        </div>
      )}

      {/* Main Action Button */}
      <div className="mb-6">
        <button 
          onClick={handleAttendanceAction}
          disabled={!!todayRecord?.checkOut}
          className={`w-full h-32 rounded-xl flex flex-col items-center justify-center transition-all shadow-lg
            ${!todayRecord ? 'bg-gradient-to-r from-blue-500 to-blue-600 text-white hover:from-blue-600 hover:to-blue-700' : 
              todayRecord.checkIn && !todayRecord.checkOut ? 'bg-gradient-to-r from-green-500 to-green-600 text-white hover:from-green-600 hover:to-green-700' : 
              'bg-gray-200 text-gray-600 cursor-not-allowed'}`}
        >
          <div className="flex items-center justify-center w-full">
            {todayRecord?.checkOut ? (
              <Check className="w-8 h-8 mr-3" />
            ) : (
              <Power className="w-8 h-8 mr-3" />
            )}
            <span className="text-2xl font-bold">{attendanceButtonText}</span>
          </div>
          <div className="mt-2 text-lg">
            {todayRecord?.checkIn && (
              <span className="mr-4">In: {todayRecord.checkIn}</span>
            )}
            {todayRecord?.checkOut && (
              <span>Out: {todayRecord.checkOut}</span>
            )}
          </div>
        </button>
      </div>

      {/* Secondary Actions */}
      <div className="grid grid-cols-2 gap-4 mb-6">
        <button 
          onClick={() => setShowLeaveDialog(true)} 
          disabled={!!todayRecord}
          className="flex items-center justify-center h-14 bg-white border border-blue-200 rounded-xl shadow-sm disabled:bg-gray-100 disabled:text-gray-400 hover:bg-blue-50 transition-colors"
        >
          <Plus className="w-5 h-5 mr-2" />
          <span className="font-medium">Request Leave</span>
        </button>
        <button 
          onClick={() => setShowHolidayDialog(true)} 
          disabled={!!todayRecord}
          className="flex items-center justify-center h-14 bg-white border border-blue-200 rounded-xl shadow-sm disabled:bg-gray-100 disabled:text-gray-400 hover:bg-blue-50 transition-colors"
        >
          <Plus className="w-5 h-5 mr-2" />
          <span className="font-medium">Mark Holiday</span>
        </button>
      </div>

      {/* Export Options */}
      <div className="mb-6 bg-white p-4 rounded-xl shadow-lg">
        <h2 className="text-lg font-medium mb-4 text-blue-800">Export Data</h2>
        <div className="grid grid-cols-1 gap-3">
          <button 
            onClick={exportToExcel} 
            className="flex items-center justify-center h-12 bg-white border border-blue-200 rounded-lg hover:bg-blue-50 transition-colors"
          >
            <FileText className="w-5 h-5 mr-2 text-blue-600" />
            <span className="font-medium">Export to Excel</span>
          </button>
          
          <button 
            onClick={shareViaWhatsApp} 
            className="flex items-center justify-center h-12 bg-white border border-blue-200 rounded-lg hover:bg-blue-50 transition-colors"
          >
            <Share2 className="w-5 h-5 mr-2 text-green-600" />
            <span className="font-medium">Share via WhatsApp</span>
          </button>
        </div>
      </div>

      {/* Today's Status */}
      <div className="mb-6 bg-white p-4 rounded-xl shadow-lg">
        <h2 className="text-lg font-medium mb-4 text-blue-800">Today's Status</h2>
        {todayRecord ? (
          <div className="space-y-3">
            <p><span className="font-medium">Date:</span> {todayRecord.date}</p>
            {todayRecord.checkIn && <p><span className="font-medium">Check In:</span> {todayRecord.checkIn}</p>}
            {todayRecord.checkOut && <p><span className="font-medium">Check Out:</span> {todayRecord.checkOut}</p>}
            {todayRecord.status === 'leave' && (
              <p><span className="font-medium">Leave Reason:</span> {todayRecord.leaveReason}</p>
            )}
            {todayRecord.status === 'holiday' && (
              <p className="font-medium text-yellow-600">Public Holiday</p>
            )}
          </div>
        ) : (
          <p className="text-gray-500">No attendance recorded for today</p>
        )}
      </div>

      {/* Recent Records */}
      <div className="bg-white p-4 rounded-xl shadow-lg">
        <h2 className="text-lg font-medium mb-4 text-blue-800">Recent Records</h2>
        {records.length > 0 ? (
          <div className="space-y-4 max-h-96 overflow-y-auto">
            {records.slice().reverse().map((record) => (
              <div key={record.id} className="border-b border-gray-200 pb-3 last:border-b-0">
                <p className="font-medium">{record.date}</p>
                <div className="flex justify-between text-sm text-gray-600 mt-1">
                  <span>{record.checkIn ? `In: ${record.checkIn}` : ''}</span>
                  <span>{record.checkOut ? `Out: ${record.checkOut}` : ''}</span>
                  <span className={`capitalize ${
                    record.status === 'leave' ? 'text-blue-600' : 
                    record.status === 'holiday' ? 'text-yellow-600' : 
                    'text-green-600'
                  }`}>
                    {record.status === 'leave' && 'On Leave'}
                    {record.status === 'holiday' && 'Holiday'}
                    {record.status === 'present' && 'Present'}
                  </span>
                </div>
              </div>
            ))}
          </div>
        ) : (
          <p className="text-gray-500">No attendance records yet</p>
        )}
      </div>

      {/* Leave Request Modal */}
      {showLeaveDialog && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50 animate-fadeIn">
          <div className="bg-white rounded-xl w-full max-w-md shadow-2xl">
            <div className="flex justify-between items-center border-b p-4">
              <h3 className="text-lg font-medium text-blue-800">Request Leave</h3>
              <button onClick={() => setShowLeaveDialog(false)} className="text-gray-500 hover:text-gray-700">
                <X className="w-5 h-5" />
              </button>
            </div>
            <div className="p-4 space-y-4">
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">Leave Type</label>
                <select 
                  value={leaveType} 
                  onChange={(e) => setLeaveType(e.target.value)}
                  className="w-full p-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
                >
                  <option value="sick">Sick Leave</option>
                  <option value="vacation">Vacation</option>
                  <option value="personal">Personal</option>
                  <option value="other">Other</option>
                </select>
              </div>
              <div>
                <label className="block text-sm font-medium text-gray-700 mb-1">Reason</label>
                <textarea
                  value={leaveReason}
                  onChange={(e) => setLeaveReason(e.target.value)}
                  className="w-full p-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-blue-500"
                  placeholder="Enter reason for leave"
                  rows={3}
                />
              </div>
            </div>
            <div className="flex justify-end space-x-2 p-4 border-t">
              <button 
                onClick={() => setShowLeaveDialog(false)} 
                className="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition-colors"
              >
                Cancel
              </button>
              <button 
                onClick={handleLeaveRequest} 
                disabled={!leaveReason.trim()}
                className="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 disabled:bg-gray-300 transition-colors"
              >
                Submit
              </button>
            </div>
          </div>
        </div>
      )}

      {/* Holiday Modal */}
      {showHolidayDialog && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50 animate-fadeIn">
          <div className="bg-white rounded-xl w-full max-w-md shadow-2xl">
            <div className="flex justify-between items-center border-b p-4">
              <h3 className="text-lg font-medium text-blue-800">Mark as Public Holiday</h3>
              <button onClick={() => setShowHolidayDialog(false)} className="text-gray-500 hover:text-gray-700">
                <X className="w-5 h-5" />
              </button>
            </div>
            <div className="p-4">
              <p>Are you sure you want to mark today as a public holiday?</p>
              <p className="text-sm text-gray-500 mt-2">This will prevent check-ins/outs for today.</p>
            </div>
            <div className="flex justify-end space-x-2 p-4 border-t">
              <button 
                onClick={() => setShowHolidayDialog(false)} 
                className="px-4 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition-colors"
              >
                Cancel
              </button>
              <button 
                onClick={handleHoliday} 
                className="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
              >
                Confirm
              </button>
            </div>
          </div>
        </div>
      )}
    </div>
  );
}

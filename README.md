## Bar Chart Using Recharts and Tailwind CSS

```tsx
import React from "react"
import {
  Bar,
  BarChart,
  CartesianGrid,
  Legend,
  ResponsiveContainer,
  Tooltip,
  XAxis,
  YAxis,
} from "recharts"

import { numberWithCommas } from "@/lib/helper"
import { cn } from "@/lib/utils"

const data = [
  {
    name: "Classroom A",
    female: 10,
    male: 21,
  },
  {
    name: "Classroom B",
    female: 15,
    male: 25,
  },
  {
    name: "Classroom C",
    female: 20,
    male: 18,
  },
  {
    name: "Classroom D",
    female: 21,
    male: 29,
  },
  {
    name: "Classroom E",
    female: 18,
    male: 18,
  },
  {
    name: "Classroom F",
    female: 22,
    male: 28,
  },
  {
    name: "Classroom G",
    female: 17,
    male: 13,
  },
]

export default function BarChartExample() {
  return (
    <ResponsiveContainer width="100%" height="100%">
      <BarChart width={500} height={300} data={data}>
        <CartesianGrid strokeDasharray="3 3" opacity={0.2} vertical={false} />
        <XAxis
          dataKey="name"
          axisLine={false}
          tickLine={false}
          stroke="#e5e5e5"
          fontSize={14}
          interval={0}
        />
        <YAxis
          axisLine={false}
          tickLine={false}
          stroke="#e5e5e5"
          fontSize={14}
        />
        <Tooltip
          wrapperStyle={{ outline: "none" }}
          cursor={{ fill: "#fafafa", opacity: "0.03" }}
          content={({ payload, label }) => {
            return (
              <div className="min-w-[8rem] divide-y divide-brand-200 rounded-md border border-brand-200 bg-brand-50 text-brand-700 shadow dark:divide-brand-700 dark:border-brand-700 dark:bg-brand-900 dark:text-brand-200">
                <p className="px-4 py-1.5">{label}</p>
                <div>
                  <ul className="px-4 py-1.5">
                    {payload.map((p, i) => {
                      return (
                        <li key={i} className="text-sm">
                          <svg
                            className={cn("mr-2 inline h-2 w-2")}
                            fill={i === 0 ? "#60a5fa" : "#f472b6"}
                            viewBox="0 0 8 8"
                          >
                            <circle cx={4} cy={4} r={4} />
                          </svg>
                          {numberWithCommas(p.value.toString())}
                        </li>
                      )
                    })}
                  </ul>
                </div>
              </div>
            )
          }}
          position={{ y: 0 }}
        />
        <Legend
          layout="horizontal"
          verticalAlign="top"
          align="center"
          content={({ payload }) => {
            return (
              <ul className="flex w-fit gap-4 pb-6 pl-1">
                {payload.map((p, i) => (
                  <li key={i}>
                    <svg
                      className={cn("mr-2 inline h-2 w-2")}
                      fill={i === 0 ? "#60a5fa" : "#f472b6"}
                      viewBox="0 0 8 8"
                    >
                      <circle cx={4} cy={4} r={4} />
                    </svg>
                    {p.value}
                  </li>
                ))}
              </ul>
            )
          }}
        />
        <Bar dataKey="male" fill="#60a5fa" radius={[3, 3, 0, 0]} />
        <Bar dataKey="female" fill="#f472b6" radius={[3, 3, 0, 0]} />
      </BarChart>
    </ResponsiveContainer>
  )
}
```

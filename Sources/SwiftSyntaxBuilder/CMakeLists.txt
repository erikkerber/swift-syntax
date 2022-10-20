# This source file is part of the Swift.org open source project
#
# Copyright (c) 2014 - 2022 Apple Inc. and the Swift project authors
# Licensed under Apache License v2.0 with Runtime Library Exception
#
# See http://swift.org/LICENSE.txt for license information
# See http://swift.org/CONTRIBUTORS.txt for Swift project authors

add_library(SwiftSyntaxBuilder STATIC
  BuildBuildable.swift
  HasTrailingComma.swift
  Indenter.swift
  Syntax+StringInterpolation.swift

  ConvenienceInitializers/BinaryOperatorExprConvenienceInitializers.swift
  ConvenienceInitializers/BooleanLiteralExprConvenienceInitializers.swift
  ConvenienceInitializers/CatchClauseConvenienceInitializer.swift
  ConvenienceInitializers/CustomAttributeConvenienceInitializers.swift
  ConvenienceInitializers/DictionaryExprConvenienceInitializers.swift
  ConvenienceInitializers/FloatLiteralExprConvenienceInitializers.swift
  ConvenienceInitializers/FunctionCallExprConvenienceInitializers.swift
  ConvenienceInitializers/IdentifierExprConvenienceInitializers.swift
  ConvenienceInitializers/IdentifierPatternConvenienceInitializers.swift
  ConvenienceInitializers/IfStmtConvenienceInitializers.swift
  ConvenienceInitializers/IntegerLiteralExprConvenienceInitializers.swift
  ConvenienceInitializers/MemberAccessExprConvenienceInitializers.swift
  ConvenienceInitializers/PrefixOperatorExprConvenienceInitializers.swift
  ConvenienceInitializers/SimpleTypeIdentifierConvenienceInitializers.swift
  ConvenienceInitializers/StringConvenienceInitializers.swift
  ConvenienceInitializers/StringLiteralExprConvenienceInitializers.swift
  ConvenienceInitializers/TernaryExprConvenienceInitializers.swift
  ConvenienceInitializers/TupleExprElementConvenienceInitializers.swift
  ConvenienceInitializers/TypeAnnotationConvenienceInitializers.swift
  ConvenienceInitializers/VariableDeclConvenienceInitializers.swift
  generated/BuildableBaseProtocols.swift
  generated/BuildableCollectionNodes.swift
  generated/BuildableNodes.swift
  generated/ExpressibleAsProtocols.swift
  generated/ResultBuildersFile.swift
  generated/Token.swift
  gyb_generated/SyntaxExpressibleByStringInterpolationConformances.swift
)

target_link_libraries(SwiftSyntaxBuilder PUBLIC
  SwiftParser
  SwiftSyntax
  )

set_property(GLOBAL APPEND PROPERTY SWIFTSYNTAX_EXPORTS SwiftSyntaxBuilder)

# NOTE: workaround for CMake not setting up include flags yet
set_target_properties(SwiftSyntaxBuilder PROPERTIES
  INTERFACE_INCLUDE_DIRECTORIES
  "${CMAKE_Swift_MODULE_DIRECTORY} ${CMAKE_CURRENT_SOURCE_DIR}")

install(TARGETS SwiftSyntaxBuilder
  EXPORT SwiftSyntaxTargets
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin)